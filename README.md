# 📋 Absensi Karyawan (QR Code)

Aplikasi absensi karyawan sederhana berbasis **scan QR Code**, berjalan langsung di browser tanpa perlu instalasi, backend, atau database eksternal. Semua data tersimpan otomatis di penyimpanan lokal browser (`localStorage`).

## ✨ Fitur

- **Data Karyawan** — tambah/hapus karyawan, tiap karyawan otomatis mendapat ID unik dan QR Code pribadi.
- **Cetak Kartu QR** — cetak kartu ID untuk semua karyawan sekaligus, siap dibagikan/ditempel.
- **Scan Absen via Kamera** — arahkan kamera ke QR karyawan untuk mencatat kehadiran:
  - Scan pertama di hari itu → tercatat sebagai **Absen Masuk**
  - Scan kedua di hari yang sama → tercatat sebagai **Absen Pulang**
  - Ada notifikasi suara (beep) dan status nama + jam setiap berhasil scan
- **Input Manual** — cadangan kalau kamera tidak bisa diakses (ketik/tempel ID karyawan).
- **Rekap Absensi** — tabel riwayat lengkap, bisa difilter per tanggal, dan diunduh ke file Excel (`.xlsx`).

## 📁 Isi Folder

```
absensi-karyawan.html   -> aplikasi utama, buka file ini di browser
README.md               -> dokumen ini
```

## 🚀 Cara Menjalankan

### Opsi 1 — Buka langsung (paling sederhana)
Cukup **double-click** file `absensi-karyawan.html`, otomatis terbuka di browser default.

> ⚠️ Catatan: fitur **kamera** butuh konteks aman (HTTPS atau `localhost`). Kalau dibuka langsung sebagai file (`file://...`), sebagian browser (terutama Chrome) akan **memblokir akses kamera**. Kalau ini terjadi, gunakan **Input Manual** di tab "Scan Absen" sebagai alternatif, atau gunakan salah satu opsi di bawah agar kamera berfungsi normal.

### Opsi 2 — Jalankan lewat server lokal (kamera pasti berfungsi)
Kalau punya Python terinstal, buka terminal di folder ini lalu jalankan:

```bash
python -m http.server 8000
```

Lalu buka `http://localhost:8000/absensi-karyawan.html` di browser.

### Opsi 3 — Hosting online gratis (bisa diakses dari HP mana saja)
Upload file `absensi-karyawan.html` ke layanan hosting statis gratis seperti:
- [Netlify Drop](https://app.netlify.com/drop) — tinggal drag & drop file-nya
- [GitHub Pages](https://pages.github.com/)
- [Vercel](https://vercel.com/)

Semua opsi ini otomatis menyediakan HTTPS, sehingga kamera bisa diakses dari perangkat apa pun (laptop maupun HP) tanpa masalah.

## 🧭 Cara Pakai

1. **Tambahkan karyawan** di tab "Data Karyawan" (nama + departemen opsional).
2. Klik **"Lihat QR"** untuk melihat/mengunduh QR Code satu karyawan, atau **"Cetak Semua Kartu QR"** untuk mencetak kartu ID semua karyawan sekaligus.
3. Bagikan/tempel kartu QR tersebut ke masing-masing karyawan (kartu nama, ID card, dsb).
4. Buka tab **"Scan Absen"**, klik **"Mulai Kamera"**, lalu arahkan kamera ke QR karyawan saat mereka datang/pulang.
5. Cek hasilnya di tab **"Rekap Absensi"** — bisa difilter per tanggal dan diunduh sebagai file Excel.

## 💾 Penyimpanan Data

Semua data (daftar karyawan & riwayat absensi) disimpan di `localStorage` browser tempat file ini dibuka. Artinya:
- Data **tidak hilang** meski browser ditutup atau komputer dimatikan.
- Data **tidak tersinkronisasi** antar perangkat/browser berbeda — kalau dibuka dari laptop dan HP secara terpisah, datanya akan berbeda.
- Menghapus cache/data browser akan **menghapus seluruh data absensi**. Disarankan mengunduh rekap ke Excel secara berkala sebagai backup.

## 🔒 Privasi

Aplikasi ini berjalan 100% di sisi klien (browser). Tidak ada data yang dikirim ke server mana pun — semuanya diproses dan disimpan lokal di perangkat tempat aplikasi dibuka.

## 🛠️ Dibangun Dengan

- HTML, CSS, JavaScript (vanilla, tanpa framework)
- [QRCode.js](https://davidshimjs.github.io/qrcodejs/) — pembuatan QR Code
- [jsQR](https://github.com/cozmo/jsQR) — pemindaian QR Code dari kamera
- [SheetJS (xlsx)](https://sheetjs.com/) — ekspor data ke Excel
