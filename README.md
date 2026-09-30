# Catatan Bimbel

Aplikasi checklist laporan belajar siswa. GitHub Pages untuk frontend, Supabase untuk autentikasi dan database.

## Fitur
- Daftar dan masuk pengajar
- Tambah, edit, hapus siswa
- Laporan per pertemuan: tanggal, mata pelajaran, materi, 5 checklist, catatan dan rencana berikutnya
- Filter laporan berdasarkan siswa dan bulan
- Ringkasan siswa, pertemuan dan pemahaman materi
- Mode contoh yang tidak menyimpan data

## Pengembangan
`npm ci` lalu `npm run dev`. Jalankan `npm run build` untuk build produksi.

Konfigurasi browser berada di `src/config.js` dan hanya berisi URL Supabase serta publishable key. Jangan memasukkan service_role atau secret key. Schema berada di `supabase/schema.sql`; seluruh tabel memiliki RLS berbasis pemilik akun.

GitHub Pages dipublikasikan otomatis dari branch `main` melalui GitHub Actions. Source Pages harus diatur ke GitHub Actions.

## Checklist dan rekap bulanan
Menu Atur checklist menyimpan template khusus per akun. Checklist setiap laporan adalah snapshot; perubahan template tidak mengubah riwayat. Rekap bulanan menyediakan filter bulan/siswa, unduhan PDF dan pesan WhatsApp. PDF dilampirkan pengguna di WhatsApp.

Pendaftaran langsung melalui Supabase Edge Function register (tidak mengirim email verifikasi); login tetap menggunakan Supabase Auth. Endpoint pendaftaran hanya menerima public API key aplikasi, membatasi percobaan per IP per jam dan tidak memperbarui akun lama. Service role hanya di Edge Function.
