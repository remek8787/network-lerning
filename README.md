# Alvii Network Learning Hub

Platform belajar jaringan modern untuk siswa SMK TKJ/ASJ dengan fokus pengalaman belajar yang nyaman, visual yang hidup, dan alur admin-siswa yang gampang diteruskan ke versi backend nanti.

## Status implementasi saat ini
Versi saat ini sudah **live** sebagai **frontend-first learning portal** dengan nuansa UI modern dan mobile-friendly.

Yang sudah berjalan:
- landing page modern dengan animasi halus, gradasi, dan layout profesional
- login admin dan siswa
- dashboard admin untuk kelola siswa sederhana
- dashboard admin untuk tambah / edit / hapus materi
- dashboard siswa untuk membaca materi
- pelacakan aktivitas siswa sederhana
- log login / logout sederhana
- ilustrasi visual untuk bantu ajar
- dukungan PWA ringan (`manifest.webmanifest` + `sw.js`)
- penyimpanan lokal via `localStorage`

## Stack versi sekarang
- HTML
- Tailwind via CDN
- Vanilla JavaScript
- PWA ringan
- Tanpa backend/database server (sementara)

## Struktur file penting
- `index.html` — aplikasi utama frontend
- `dsg-topology.html` — halaman detail materi topologi DSG
- `manifest.webmanifest` — konfigurasi PWA
- `sw.js` — service worker ringan
- `images/illustrations/` — aset ilustrasi / diagram buatan internal
- `images/materials/` — aset materi nyata / upload lapangan
- `images/materials/topology/` — materi gambar topologi
- `images/materials/ip/` — materi gambar IP address dan subnet
- `images/materials/mikrotik/` — materi gambar terkait MikroTik

## Akun demo default
- Admin: `admin` / `admin123`
- Siswa: `siswa` / `siswa123`

## Catatan penting UI/UX
- kredensial admin **tidak ditampilkan** di antarmuka login
- tampilan diarahkan ke gaya semi-dark premium yang tetap nyaman dibaca
- fokus utama versi ini: bikin siswa betah baca dan admin enak ngatur materi dasar

## Batasan versi sekarang
Karena masih frontend-first:
- data tersimpan di browser perangkat yang dipakai
- belum multi-user sungguhan
- belum ada backend auth real
- belum ada database online
- jika cache/browser dibersihkan, data lokal bisa ikut hilang

## Rekomendasi tahap lanjut
Urutan paling masuk akal setelah versi ini:
1. pindah dari `localStorage` ke backend + database
2. buat role dan autentikasi real
3. tambah halaman detail materi per topik
4. tambah upload gambar / PDF / video / referensi
5. tambah kuis, progres belajar, dan validasi pemahaman
6. tambah laporan mentor / pembimbing

## Deploy catatan penting
Project ini pernah di-upload ke hosting lewat FTP mirror.

Pelajaran penting:
- **jangan hapus `.well-known` saat sinkronisasi deploy**
- jika pakai `lftp mirror -R --delete`, wajib beri exclude untuk `.well-known`

Contoh aman:
```bash
mirror -R --verbose \
  --exclude-glob .git \
  --exclude-glob .git/** \
  --exclude-glob .well-known \
  --exclude-glob .well-known/** \
  ./ ./
```

## Konvensi aset gambar
Agar hosting dan repo tetap rapi, gunakan aturan ini untuk aset baru:

- semua nama file pakai **huruf kecil + kebab-case**
- hindari spasi pada nama file
- pisahkan berdasarkan fungsi:
  - `images/illustrations/` → ikon, diagram, SVG buatan internal
  - `images/materials/topology/` → topologi lapangan / topologi pembelajaran
  - `images/materials/ip/` → materi IP, subnet, addressing
  - `images/materials/mikrotik/` → materi MikroTik / router
- contoh nama yang benar:
  - `topologi-dsg.png`
  - `dasar-ip-address.png`
  - `dasar-ip-address-per-class.png`

## Arah produk
Portal ini cocok dijadikan pondasi untuk aplikasi pembelajaran jaringan bertahap, terutama untuk siswa yang fundamentalnya masih lemah dan perlu jembatan dari konsep dasar ke praktik lapangan.
