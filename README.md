# ARJUNA KOST PAKAM

**Smart Living & Services — Frontend Prototype v2**  
Website responsive dan interaktif untuk ARJUNA KOST PAKAM, dengan satu landing page yang membuka lima layanan utama: **Toko Arjuna, Laundry Arjuna, Kost Arjuna, Restaurant Arjuna, dan Customer Service**.

> **Status: PROTOTIPE / DEMO.** Semua gambar adalah visual konsep, bukan dokumentasi lokasi. Harga, menu, stok, jadwal, dan ongkos kirim adalah data ilustrasi. Formulir hanya menyimpan data pada browser yang dipakai; **belum mengirim pesanan nyata, belum mengirim laporan ke pengelola, dan belum menerima pembayaran.** Jangan gunakan untuk transaksi pelanggan sebelum backend dan keamanan siap.

## Fitur yang bisa dicoba

| Halaman | Fitur UI demo |
|---|---|
| Beranda | Brand hero dan lima pilihan layanan, navigasi mobile |
| Toko Arjuna | Kategori, pencarian instan, tambah/kurangi produk, keranjang, checkout demo |
| Laundry Arjuna | Pilih paket, berat, jadwal, lokasi gedung, estimasi biaya, formulir demo |
| Kost Arjuna | Informasi dua gedung, total 30 kamar, jalur pertanyaan kamar dan maintenance |
| Restaurant Arjuna | Kategori makanan/minuman, pencarian, keranjang dan checkout demo |
| Customer Service | Kategori layanan, prioritas, formulir laporan, FAQ, nomor tiket demo |
| Aktivitas Saya | Riwayat pesanan dan tiket simulasi dari browser yang sama |
| Panel Demo | Lihat semua data lokal dan ubah status simulasi pesanan/tiket |

**Fitur penting belum live:** login penghuni, penagihan sewa, sistem stok real-time, pembayaran QRIS/payment gateway, pengiriman WhatsApp, multi-user/multi-device, akses admin terproteksi, dan penugasan mitra yang sesungguhnya.

## Cara membuka website

1. Ekstrak file ZIP proyek.
2. Buka **`index.html`** memakai Chrome, Edge, atau browser modern.
3. Klik salah satu dari lima layanan pada beranda.
4. Untuk mencoba hubungan antar-halaman, buat pesanan/laporan demo, buka **Aktivitas Saya**, lalu **Panel Demo**.

Tidak diperlukan `npm install`, build, database, atau server untuk meninjau UI. Untuk pengembangan lokal yang lebih representatif, Anda bisa menjalankan server sederhana:

```sh
# dari folder proyek
python -m http.server 8080
# buka http://localhost:8080
```

## Cara upload ke GitHub Pages

### Opsi sederhana: upload manual

1. Buat repositori GitHub, contoh **`arjuna-kost-pakam`**.
2. Pilih **Add file → Upload files** di halaman repositori.
3. Unggah isi folder proyek, **bukan ZIP-nya**. Pastikan `index.html` ada di root repositori, dan folder `assets/` tetap bersama file lainnya.
4. Commit perubahan.
5. Buka **Settings → Pages → Build and deployment**.
6. Pada **Source**, pilih **Deploy from a branch**. Pilih branch `main`, folder `/ (root)`, lalu **Save**.
7. Tunggu GitHub Pages selesai deploy. URL umumnya seperti `https://USERNAME.github.io/arjuna-kost-pakam/`.

Navigasi memakai URL hash (`#/toko`, `#/laundry`, dan seterusnya), sehingga halaman berfungsi di GitHub Pages tanpa konfigurasi rewrite atau backend.

### Opsi melalui Git

```sh
git init
git add .
git commit -m "Initial ARJUNA KOST PAKAM website"
git branch -M main
git remote add origin https://github.com/USERNAME/arjuna-kost-pakam.git
git push -u origin main
```

Ganti `USERNAME` sesuai akun GitHub Anda dan buat repo kosong sebelumnya.

## Struktur proyek

```text
ARJUNA-KOST-PAKAM/
├── index.html               # Meta, title, font, app root
├── styles.css               # Design system, desktop dan mobile UI
├── app.js                   # Konten, data demo, router dan interaksi
├── manifest.webmanifest     # Metadata shortcut mobile
├── .nojekyll                # Kompatibilitas GitHub Pages
├── robots.txt               # Mode staging: cegah indeks demo
├── README.md                # Dokumentasi ini
└── assets/
    ├── favicon.svg
    ├── og-cover.jpg
    ├── toko.webp
    ├── laundry.webp
    ├── kost.webp
    ├── restaurant.webp
    ├── support.webp
    └── room-wide.webp
```

## Mengganti konten

Buka `app.js` menggunakan VS Code atau editor teks.

- **Nama/urutan layanan:** array `services`.
- **Daftar produk Toko Arjuna:** array `products.toko`.
- **Menu Restaurant Arjuna:** array `products.restaurant`.
- **Harga dan paket Laundry:** array `laundryPlans`.
- **Informasi gedung, fasilitas, 30 kamar:** fungsi `kostPage()`.
- **Pertanyaan umum dan informasi kontak:** fungsi `supportPage()`.
- **Judul dan warna:** `index.html` / variabel CSS pada awal `styles.css`.
- **Foto konsep:** ganti file `.webp` pada `assets/` dengan foto sebenarnya (pertahankan namanya, atau ubah referensi file di `app.js`).

Sebelum publikasi layanan nyata, tambahkan nomor kontak, jam operasional, alamat lengkap terverifikasi, fasilitas kamar sebenarnya, ongkos kirim, ketentuan pengembalian, dan harga yang sudah disetujui mitra.

## Penyimpanan demo

Data pesanan, tiket, dan keranjang menggunakan `localStorage` dengan prefix `arjuna_v2_`.

- Data hanya terlihat pada **browser/perangkat yang sama**.
- Tidak ada autentikasi atau backend.
- Data bisa hilang setelah browser dibersihkan.
- Panel Demo **bukan panel admin sungguhan** dan tidak boleh menyimpan data rahasia.
- Tombol **Reset Demo** menghapus simulasi pada browser tersebut.

## Rekomendasi fase produksi

1. **Database dan identitas pengguna:** buat struktur `buildings`, `rooms`, `residents`, `partners`, `products`, `orders`, `order_items`, `tickets`, `invoices`, `payments`, `service_assignments`.
2. **Hak akses:** pemilik, admin, penghuni, dan mitra harus punya otorisasi berbeda; jangan membuka data pribadi di sisi frontend.
3. **Order engine:** harga dan stok dihitung ulang di server; order memiliki status, audit log, dan penanggung jawab.
4. **Pembayaran:** gateway resmi di backend, verifikasi webhook server-side, rekonsiliasi, refund, dan pencairan mitra sesuai kontrak.
5. **Service Assurance:** SLA yang disetujui, kategori masalah, bukti, eskalasi, hak kompensasi, dan log penyelesaian.
6. **Peluncuran publik:** domain, HTTPS, pengujian keamanan, dokumen privasi, syarat layanan, legalitas yang relevan, dan penghapusan penanda demo.

**Jangan pernah menaruh API secret, token payment gateway, atau kunci database tingkat admin di `app.js` atau repo publik.**

## Informasi desain

- Gaya: **Clean Premium × Gen Z Lifestyle**.
- Palet: deep emerald `#083e33`, warm cream `#faf9f5`, muted gold `#bc9756`.
- Fokus UX: lima pintu masuk yang jelas, mobile-first, CTA tegas, sedikit pilihan sekaligus, dan proses singkat.
- Semua foto saat ini adalah ilustrasi visual berbasis AI yang dibuat untuk demonstrasi konsep; jangan dipakai sebagai bukti bentuk asli gedung/toko/restoran.
- Teks demo sengaja menghindari klaim jam buka, fasilitas, atau harga resmi yang belum ditetapkan.

---

Proyek ini disiapkan sebagai fondasi desain dan uji pengalaman pengguna ARJUNA KOST PAKAM. Perubahan menjadi layanan produksi memerlukan integrasi backend dan pengesahan aturan operasional.
