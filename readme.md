#  FolderAnalyzer

Aplikasi desktop ringan untuk **analisis kapasitas penyimpanan** dan **pencarian file duplikat** berbasis hash MD5. Dibangun dengan Python & Tkinter, bersifat **fully portable** dan tidak memerlukan instalasi Python atau dependensi tambahan di komputer target.

---

## ✨ Fitur Utama

| Fitur | Deskripsi |
|-------|-----------|
| 📊 **Dual Mode** | Pilih antara `Analisis Kapasitas` atau `Cari Duplikat (MD5)` sebelum scan |
| 🌳 **Tree View Hierarkis** | Visualisasi struktur folder dengan indentasi & kalkulasi ukuran otomatis |
|  **Deteksi Duplikat MD5** | Optimasi berbasis filter ukuran file → hanya hash file yang identik (cepat & hemat memori) |
| 🖱️ **Interaksi Cerdas** | Klik 2x folder → Expand/Collapse • Klik 2x file → Buka default app • Klik kanan → Context menu |
| ⏱️ **Progress Real-time** | Progress bar determinate (%) + tombol `Hentikan` yang aman tanpa crash |
| 🗑️ **Hapus Selektif** | Hapus file/folder langsung dari tree. Ukuran parent ter-update otomatis |
| 📦 **Portable** | Distribusi via PyInstaller (`dist/`), siap pakai di Windows tanpa Python |

---

## 📘 Manual Penggunaan

### 1️⃣ Persiapan
1. Ekstrak folder `FolderAnalyzer` ke lokasi mana pun (Desktop, D:, Flashdisk, dll)
2. Buka folder → double-click `FolderAnalyzer.exe`
3. Aplikasi akan terbuka dalam 1-3 detik (startup normal untuk mode `onedir`)

### 2️⃣ Memilih Mode Operasi
Di bagian atas jendela, pilih salah satu mode:
- 📊 **Analisis Kapasitas** → Untuk melihat struktur folder, ukuran file, dan hierarchy penyimpanan
- 🔍 **Cari Duplikat (MD5)** → Untuk menemukan file identik berdasarkan konten (bukan nama)

> ⚠️ Mode hanya bisa diubah **sebelum** klik `Mulai Analisis`.

### 3️⃣ Mode Analisis Kapasitas
| Aksi | Cara |
|------|------|
| **Mulai Scan** | Masukkan path folder → klik `▶️ Mulai Analisis` |
| **Expand/Collapse Folder** | Klik 2x pada baris folder, atau klik ikon `▶/▼` di kiri |
| **Buka File** | Klik 2x pada baris file → terbuka dengan aplikasi default Windows |
| **Urutkan Kolom** | Klik header `Nama`, `Tipe`, `Ukuran`, atau `Path` (toggle Asc/Desc) |
| **Hapus Item** | Klik kanan pada item → `🗑️ Hapus File/Folder` → konfirmasi |
| **Hentikan Scan** | Klik `⛔ Hentikan` (aman, tidak merusak data) |

📌 **Catatan Ukuran Folder**: Ukuran folder dihitung secara bottom-up (total semua file & subfolder di dalamnya). Saat Anda menghapus file, ukuran parent akan ter-update otomatis.

### 4️⃣ Mode Pencarian Duplikat (MD5)
1. Pilih mode `🔍 Cari Duplikat (MD5)`
2. Masukkan path → klik `▶️ Mulai Analisis`
3. Aplikasi akan:
   - Mengelompokkan file berdasarkan ukuran byte
   - Hanya menghitung MD5 untuk file yang ukurannya sama (optimasi kecepatan)
   - Menampilkan grup duplikat dengan hash, jumlah, ukuran, dan contoh lokasi
4. **Menghapus Duplikat**:
   - Klik baris grup duplikat di tabel
   - Tombol `️ Hapus Duplikat` akan aktif
   - Klik → konfirmasi → file pertama dalam grup akan dihapus permanen
   - Jika grup tersisa 1 file, baris otomatis hilang

### 5️⃣ Interaksi & Shortcuts
| Mouse/Keyboard | Fungsi |
|----------------|--------|
| `Double Click` (Folder) | Toggle Expand/Collapse |
| `Double Click` (File) | Open with default application |
| `Right Click` | Buka context menu (Expand/Hapus) |
| `Header Column Click` | Sort Ascending/Descending |
| `⛔ Hentikan` | Safe-cancel thread background |

---

## 🛠️ Build dari Source / Compile ke `.EXE`

Jika Anda ingin memodifikasi kode atau compile ulang setelah update:

### Prasyarat
- Python 3.8+
- Terminal PowerShell atau CMD

### Langkah Build (1x Setup)
```powershell
# Buat environment lokal di folder project
conda create --prefix .\build_env python=3.12 -y
.\build_env\Scripts\pip.exe install pyinstaller
