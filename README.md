# anam12retail.pro - Panduan Pasang di GitHub, HP, dan Sinkron Data

Login awal: **pusat / pusat123** (Pusat) dan **kasir / kasir123** (Kasir). Segera ganti sandi di menu *Akun Saya*.

## A. Pindah ke GitHub (tanpa perlu install apa pun)
1. Ekstrak file ZIP. Isinya: `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`, `README.md`.
2. Buka https://github.com dan daftar / masuk.
3. Klik tanda **+** (kanan atas) > **New repository**.
4. Isi *Repository name*: `anam12retail`. Pilih **Public**. Klik **Create repository**.
5. Di halaman repositori klik **uploading an existing file**.
6. Seret SEMUA file hasil ekstrak ke halaman itu (jangan seret foldernya, seret isinya). Nama `index.html` jangan diubah.
7. Klik **Commit changes**.
8. Buka **Settings** > **Pages** (menu kiri).
9. Di *Build and deployment*, *Source* pilih **Deploy from a branch**. Branch pilih **main**, folder **/ (root)**. Klik **Save**.
10. Tunggu 1-2 menit lalu muat ulang halaman Pages. Alamat aplikasi muncul: `https://NAMAANDA.github.io/anam12retail/`.

Memperbarui aplikasi nanti: buka repositori > **Add file** > **Upload files** > timpa `index.html` > **Commit changes**.

## B. Login dari HP
1. Buka alamat GitHub Pages di Chrome (Android) atau Safari (iPhone).
2. Login seperti biasa.
3. Pasang seperti aplikasi: Android: menu titik tiga > **Instal aplikasi**. iPhone: tombol Bagikan > **Tambah ke Layar Utama**.

Catatan: tanpa langkah C, data HP dan komputer terpisah.

## C. Data sama di HP dan komputer (Firebase, gratis)
1. Buka https://console.firebase.google.com > **Create a project**.
2. Menu **Build** > **Realtime Database** > **Create Database**. Pilih lokasi Singapore, mode **locked**.
3. Tab **Rules**, ganti isinya dengan teks ini lalu **Publish**:
```
{"rules":{".read":false,".write":false,"$k":{".read":true,".write":true}}}
```
4. Tab **Data**: salin URL di bagian atas (berawalan https://, berakhiran firebasedatabase.app).
5. Di anam12retail.pro login sebagai Pusat > **Pengaturan** > **Atur Sinkron**. Isi URL tadi dan **Kunci rahasia** buatan Anda (acak, 16 karakter atau lebih, mis. `tokoSaya-8f3kQ29xLm71`). Simpan.
6. Di HP dan komputer lain lakukan langkah 5 dengan URL dan kunci yang SAMA. Data lalu tersinkron tiap sekitar 20 detik.

## Batasan penting
- Siapa pun yang tahu URL + kunci rahasia bisa membaca dan mengubah data (termasuk sandi). Jangan bagikan kunci itu.
- Sinkron memakai sistem "yang terakhir menyimpan menang". Jika dua kasir berjualan bersamaan, sebagian transaksi bisa tertimpa. Cocok untuk satu kasir utama + pemilik memantau dari HP.
- Data tetap tersimpan lokal di tiap perangkat. Lakukan **Pengaturan > Backup** secara rutin.
- Lupa sandi: lakukan Restore dari backup, atau hapus data situs di browser (data lokal hilang).

## D. Memakai domain anam12retail.pro (opsional)
Domain harus dibeli dulu di penyedia domain (mis. Niagahoster, Namecheap, Cloudflare); ketersediaan dan harga `.pro` dicek di sana. Setelah punya domain:
1. Di pengelola DNS domain, tambahkan 4 record **A** untuk `@` ke: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.
2. Tambahkan record **CNAME** untuk `www` ke `NAMAANDA.github.io`.
3. Di GitHub: repositori > **Settings > Pages > Custom domain**, isi `anam12retail.pro`, **Save**, lalu centang **Enforce HTTPS** jika sudah muncul.
4. Tunggu hingga DNS aktif (beberapa menit sampai beberapa jam). Aplikasi lalu terbuka di https://anam12retail.pro
Catatan: data lokal di browser terpisah per alamat. Pindahkan lewat **Pengaturan > Backup** lalu **Restore**.
