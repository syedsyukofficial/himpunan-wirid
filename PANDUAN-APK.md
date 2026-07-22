# Panduan: Himpunan Wirid & Hizib → APK (PWABuilder → APKPure)

Pek ini mengandungi:
- `index.html` — app utama (sudah disuntik manifest link + service worker registration)
- `manifest.json` — metadata PWA
- `service-worker.js` — cache offline (app shell)
- `icons/icon-192.png`, `icons/icon-512.png`, `icons/icon-512-maskable.png`

## Langkah 1 — Hos di GitHub Pages
1. Buat/guna repo GitHub sedia ada (cth. `Himpunan-Zikir-Wirid`).
2. Upload kesemua fail dalam folder ini (kekalkan struktur: `index.html`, `manifest.json`, `service-worker.js`, `icons/`) ke root repo.
3. Settings → Pages → pilih branch `main` / folder `root` → Save.
4. Tunggu ~1 minit, URL akan jadi seperti:
   `https://<username>.github.io/<repo>/`
5. Buka URL tu di Chrome — pastikan app load dan tiada error di DevTools Console.

## Langkah 2 — Sahkan PWA sah (penting sebelum PWABuilder)
Buka Chrome DevTools → tab **Application** → **Manifest**:
- Pastikan tiada ralat merah.
- Pastikan `icons` dua-dua size (192, 512) detect.
- Tab **Service Workers** → pastikan status "activated and running".

## Langkah 3 — PWABuilder → jana APK
1. Pergi ke **pwabuilder.com**.
2. Masukkan URL GitHub Pages anda → Start.
3. Tunggu scan siap (manifest ✅, service worker ✅, icons ✅).
4. Klik **Package for Stores** → pilih **Android**.
5. **PENTING (nota dari kerja lepas):**
   - Tab **"Other Android"** = untuk hasilkan APK yang **sudah signed**, boleh terus install pada telefon / upload ke APKPure.
   - Tab **"Google Play"** = hasilkan package **unsigned**, untuk submission ke Play Store sahaja — bukan untuk APKPure.
   - Jadi untuk tujuan anda (APKPure), pilih **"Other Android"**.
6. Isi package ID (cth. `com.syedsyuk.himpunanwirid`), version, app name.
7. Download package — anda akan dapat fail `.apk` (signed) terus, atau `.aab` + keystore bergantung pilihan. Untuk APKPure, anda perlukan `.apk` signed.
8. Install APK tu pada telefon Android dahulu untuk test (mungkin perlu benarkan "Install from unknown sources").

## Langkah 4 — Upload ke APKPure
1. Daftar akaun developer di **apkpure.com** (guna emel).
2. Dashboard → **Upload App** → upload fail `.apk` (signed) dari Langkah 3.
3. Lengkapkan maklumat:
   - Nama app: Himpunan Wirid & Hizib
   - Kategori: Lifestyle / Books & Reference / Education
   - Screenshot (ambil screenshot dari telefon semasa app dibuka — minimum 2-3 keping)
   - Ikon app (guna `icons/icon-512.png`)
   - Penerangan ringkas (Bahasa Melayu) tentang kandungan: Al-Mathurat, Hizib Bahar, Hizib Nawawi, Wirid Sakran, Hizib Nasr, Wirdul Latif, Ratib Al-Attas, Ratib Al-Haddad, Tahlil Arwah, Yasin & Doa.
   - Privacy policy URL — jika tiada, boleh guna satu laman ringkas (app ni tak kutip data pengguna, jadi ayat mudah pun cukup — boleh saya sediakan jika perlu).
4. Submit untuk review APKPure (biasanya beberapa hari).

## Nota penting
- Setiap kali anda update `index.html`, naikkan `CACHE_NAME` version dalam `service-worker.js` (cth. `himpunan-wirid-v2`) supaya pengguna dapat versi terbaru, bukan versi cache lama.
- Jika nak tukar package name / ikon selepas generate APK pertama, anda perlu re-generate dari PWABuilder semula (package name tak boleh tukar selepas publish).
