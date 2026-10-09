# RCU-Panel-System

# 👑 RCU Admin & Automation System (v0.0.2)

> **Enterprise-Grade Roblox Automation Suite & Key Gateway System**  
> *Author:* `aceu9922` | *Language:* `Lua 5.1 / Luau` | *Platform:* Roblox Desktop & Mobile

---

## 📑 Daftar Isi
- [Arsitektur Sistem (2-Tier Architecture)](#-arsitektur-sistem-2-tier-architecture)
- [Cara Penggunaan (Quick Start)](#-cara-penggunaan-quick-start)
- [Sistem Key & Monetisasi (LootLabs)](#-sistem-key--monetisasi-lootlabs)
- [Daftar Lengkap Fitur & Modul (22 Kategori)](#-daftar-lengkap-fitur--modul-22-kategori)
- [Panduan Setup & Deploy ke GitHub](#-panduan-setup--deploy-ke-github)
- [Kompatibilitas Executor & Performa](#-kompatibilitas-executor--performa)
- [Struktur File Proyek](#-struktur-file-proyek)

---

## 🏛️ Arsitektur Sistem (2-Tier Architecture)

Sistem ini didesain menggunakan arsitektur modular 2 file untuk mengoptimalkan keamanan, kecepatan pemuatan, dan integrasi monetisasi linkvertise/lootlabs:

```
[ PENGGUNA ]
     │
     ▼ Eksekusi 1-Baris Loadstring
┌──────────────────────────────────────────────────────────────┐
│  Tier 1: Loader.lua (Key Gateway & Auth Client)               │
│  - Cek Cache Lokal ("AdminPanel_SavedKey.txt")               │
│  - Jika Key Valid: Langsung Bypass UI & Load Script Utama     │
│  - Jika Belum/Expired: Tampilkan Cyberpunk Key System UI     │
│  - Verifikasi Key via GitHub Raw / Static Keys               │
└──────────────────────────────┬───────────────────────────────┘
                               │ (Key Berhasil Diverifikasi)
                               ▼
┌──────────────────────────────────────────────────────────────┐
│  Tier 2: AdminPanel_aceu9922.lua (Main Panel Script)         │
│  - 100% In-Memory Execution (Tidak tersimpan di disk)        │
│  - Dynamic Knit Framework Introspection                      │
│  - 22 Modul Otomatisasi Lengkap & Fast Teleports             │
└──────────────────────────────────────────────────────────────┘
```

---

## 🚀 Cara Penggunaan (Quick Start)

### 1. Eksekusi Publik (Via Loader + Key System)
Cukup jalankan 1 baris berikut di executor Anda:

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/USERNAME/REPOSITORY/main/Loader.lua?t=" .. tostring(tick())))()
```
> **Catatan:** Parameter `?t=<tick>` wajib disertakan untuk mem-bypass cache CDN GitHub agar script selalu mendapatkan versi terbaru secara real-time.

### 2. Eksekusi Khusus Developer (Direct Loadstring)
Untuk pemilik/developer yang terdaftar di whitelist:

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/USERNAME/REPOSITORY/main/AdminPanel_aceu9922.lua?t=" .. tostring(tick())))()
```

---

## 🔑 Sistem Key & Monetisasi (LootLabs)

### Alur Pengguna (User Flow):
1. Pengguna menjalankan script loader di executor.
2. Loader otomatis mengecek apakah ada file cache key lokal (`AdminPanel_SavedKey.txt`).
   * **Sudah pernah login & key valid:** Loader langsung mengunduh dan membuka script utama tanpa menampilkan jendela key.
   * **Belum login / key baru:** Jendela **Cyberpunk Key Gateway** akan muncul di layar.
3. Pengguna menekan tombol **`📋 Get Key (Copy Link)`**:
   * Link LootLabs/Linkvertise otomatis tersalin ke clipboard.
4. Pengguna menyelesaikan tautan LootLabs di browser untuk mendapatkan access key harian.
5. Pengguna kembali ke game, menekan tombol **`PASTE`**, lalu menekan **`🚀 Verify & Launch`**.
6. Sistem memvalidasi key secara real-time ke file [`current_keys.txt`](current_keys.txt) di GitHub. Jika cocok, key disimpan ke disk lokal dan panel utama diluncurkan.

### Cara Rotasi Key Harian/Mingguan:
Cukup edit baris string di file [`current_keys.txt`](current_keys.txt) pada repository GitHub Anda. Semua pengguna otomatis wajib memperbarui key mereka sesuai daftar baru tanpa Anda perlu mengubah atau meng-obfuscate ulang `Loader.lua`.

---

## 🛠️ Daftar Lengkap Fitur & Modul (22 Kategori)

### 1. 🌾 Farm & Celestial Drops
* **Auto Collect Farms & Harvest Ready Farms:** Otomatis memanen dan mengklaim seluruh plot farming.
* **Auto Collect Orbs:** Mengumpulkan drop orbs di sekitar map secara otomatis.
* **Auto Collect Falling Stars:** Mendeteksi dan mengklaim bintang jatuh di seluruh server.
* **Auto Mine Meteors:** Auto teleport dan mining meteorit celestial yang jatuh.

### 2. 📦 Chests & Wheels
* **Normal & Mini Chests Claim:** Auto claim semua chest tersembunyi dan mini chest di map.
* **Playtime Rewards:** Klaim reward waktu bermain tier 1–12 secara otomatis.
* **4x Auto Spin Wheels:** Otomatis memutar 4 jenis roda keberuntungan (Normal Wheel, VIP Wheel, Pet Wheel, Relic Wheel).

### 3. 🥚 Egg Hatching & Filter
* **Auto Hatch Egg (x1 / x3 / Multiplier):** Buka egg secara otomatis tanpa delay.
* **Egg Search & Teleport:** Pencarian egg berdasarkan nama area/jenis.
* **Hide Hatch Animation Overlay:** Menghapus efek visual hatching untuk menghemat FPS dan meningkatkan kecepatan buka egg hingga 300%.

### 4. ⚔️ Dungeon & Smart Pet Equipped
* **Auto Dungeon System:** Otomatis memasuki antrean dungeon, teleport ke arena, menyerang monster, dan auto-restart ronde berikutnya.
* **🐾 Smart Auto Equip Pet Dungeon:** Algoritma cerdas yang mendeteksi damage tertinggi dungeon dari seluruh inventory pet dan otomatis memasangnya sebelum dungeon dimulai.
* **Dungeon Difficulty Selector:** Mendukung tingkat kesulitan dari *Basic* hingga *Impossible*.
* **Dungeon Multiplier Bypass:** Membuka multiplier koin dungeon maksimal (hingga 4.12x multiplier).
* **Auto Critical Tap & Powerups:** Otomatis tap critical strike 100% akurat.

### 5. 🌳 Tree & Leaf Event
* **Fast Auto Rake Leaves:** Auto sapu daun event secara instan.
* **Auto Upgrade EXP Multiplier:** Otomatis upgrade level pohon dan multiplier EXP.
* **Auto Farm & Claim Tree:** Klaim reward panen pohon secara otomatis.
* **Tree Multiplier Bypass:** Memaksimalkan rate panen daun dan buah.

### 6. 🎪 Carnival & Circus
* **Circus HighStriker Ticket Farm:** Minigame HighStriker dengan **100% Perfect Accuracy Hook** (selalu mendapatkan skor jackpot 10/10).
* **Auto Play Carnival Minigames:** Otomatis memainkan mini game karnaval.
* **Safe Tier Cashout:** Penarikan tiket otomatis sebelum batas waktu habis.

### 7. 🎣 Fishing System
* **Auto Catch Fish:** Otomatis strike dan reel pancing tanpa gagal.
* **Auto Sell Fish:** Otomatis menjual ikan saat inventory penuh.
* **Auto Rod & Bait Upgrade:** Beli joran dan umpan terbaik secara otomatis.

### 8. ⛏️ Mining System
* **Auto Mine Ores:** Mining batu dan mineral langka secara instan.
* **Auto Sell Ores:** Auto jual hasil tambang ke merchant.
* **Pickaxe Upgrades:** Otomatis membeli beliung (pickaxe) tier tertinggi.

### 9. 🧪 Buffs, Potions & Fruits
* **Auto Drink Potions:** Mengonsumsi ramuan buff secara otomatis saat durasi habis.
* **Auto Eat Fruits:** Memakan buah boost stat otomatis.
* **Auto Upgrade Relics & Relic Wheel:** Meningkatkan level relik dan auto roll roda relik.

### 10. 🐶 Pet Crafting & Adventures
* **Auto Craft Tiers:** Mendukung pembuatan pet Golden, Rainbow, Void, **Galaxy**, dan Ascended.
* **Smart Pet Adventures:**
  * Algoritma deployment otomatis berdasarkan poin tier pet tertinggi.
  * Auto claim hasil adventure saat selesai.
  * Auto upgrade slot ekspedisi pet.

### 11. 🐝 Bee & Skylands
* **Auto Hive Claim:** Otomatis klaim madu dari sarang lebah.
* **Auto Flower Pollination:** Polinasi bunga otomatis di map Skylands.
* **Auto Upgrade Bee Slots:** Menambah kapasitas lebah otomatis.

### 12. 🎁 Rewards & Quests
* **Auto Claim Quests:** Daily Quests, Weekly Quests, dan Master Quests.
* **Achievements & Challenges:** Klaim otomatis badge pencapaian dan tantangan harian.
* **Miner & Angel Quests:** Otomatis menyelesaikan tier quest khusus.

### 13–18. 🏪 Remote Automated Merchants
Akses dan pembelian toko merchant otomatis tanpa harus berjalan ke lokasi NPC:
* 🚂 **Merchant Train:** Membeli kartu rotasi diskon per jam, tiket trade, dan telur langka.
* 🏺 **Ancient Merchant:** Membeli slot toko kuno (rotasi 3 jam).
* ⛏️ **Underground Market:** Membeli stok tambang bawah tanah (rotasi 10 menit, Map 20).
* 🐝 **Honey Merchant:** Membeli item menggunakan mata uang madu (Map 38 Skylands).
* 💀 **Dungeon Merchant:** Membeli item menggunakan dungeon coins (Map 15).
* 🌀 **Paradox Merchant:** Membeli kompas dan barang langka (Map 49 Paradox).

### 19. 🎫 Season Pass
* **Auto Claim Free & Premium Tiers:** Mengklaim semua tier battle pass secara otomatis.
* **Auto Reset Pass:** Reset season pass otomatis tanpa memerlukan perk Ancient Shop.
* **Claim All Tiers Instantly:** Tombol klaim cepat sekali klik untuk semua hadiah yang terbuka.
* **Live Tier Telemetry:** Menampilkan progres tier dan exp pass saat ini.

### 20. 🔨 Remote Forge & Machines
* 🌙 **Lunar Forge:**
  * Pilihan Meteorite: Normal, Magic, Fire, Void, Alien.
  * Custom Amount input (Default: 1).
  * Auto Craft otomatis.
* ⚙️ **Steampunk Machine:**
  * Pilihan Boost: Clicks, Gems, Luck, Hatch Speed, Secrets, Eggs Open.
  * Material selector dengan indikator sisa stok real-time.
  * Custom Amount input & Auto Upgrade.
* 🔮 **Fragments Forge:**
  * Mendukung 25 resep fragmen unik dengan Custom Amount & Auto Forge.

### 21. 🎲 Aura & Dice Roller
* **Dice Selector:** Menampilkan sisa jumlah dadu secara live `[Nama Dadu] (x[Jumlah])`.
* **Auto Roll Toggle:** Roll dadu otomatis.
* **Disable Rolling Animation:** Bypass animasi lempar dadu untuk hasil instan tanpa delay.
* **Auto Craft Aura Dice:** Otomatis menggabungkan dadu tier rendah ke tier tinggi.

### 22. 📊 System, Telemetry & Teleport
* **Live Player Telemetry:** Memantau koin, gems, exp, dan status multiplier secara live.
* **Fast Teleports with Search:** Menu teleportasi cepat ke seluruh map/dunia dengan fitur pencarian real-time.
* **Custom Totem Spawner & Inventory Tracker:** Cek total totem di tas dan spawn dengan kustomisasi jumlah.
* **Security Whitelist Guard:** Proteksi eksekusi berbasis username developer (`aceu9922`).

---

## ⚙️ Panduan Setup & Deploy ke GitHub

1. Buat repository baru di [GitHub](https://github.com) (publik atau privat).
2. Upload file berikut:
   * [`AdminPanel_aceu9922.lua`](AdminPanel_aceu9922.lua)
   * [`Loader.lua`](Loader.lua)
   * [`current_keys.txt`](current_keys.txt)
3. Buka file [`Loader.lua`](Loader.lua), lalu perbarui URL di bagian `CONFIG` (baris 16–41):
   * Ubah `MainScriptURL` ke URL Raw `AdminPanel_aceu9922.lua` Anda.
   * Ubah `KeyListURL` ke URL Raw `current_keys.txt` Anda.
   * Masukkan link monetisasi LootLabs Anda pada `LootLabsLink`.
4. Simpan dan commit. Bagikan link eksekusi `Loader.lua` kepada publik!

---

## 🔒 Kompatibilitas Executor & Performa

* **Kompatibilitas Bahasa:** Murni **Lua 5.1** dan **Luau** (Bebas dari operator majemuk `+=`, `-=`, dan keyword `continue`).
* **Knit Framework Resolver:** Menggunakan introspeksi dinamis `safeRequire` dengan thread identity switching (Level 2) agar aman dari deteksi script Roblox core.
* **Batas Variabel:** Variabel lokal global dioptimalkan pada 177 dari batas maksimal 200 locals Luau.
* **Dukungan Executor:**
  * ✅ Synapse Z / Wave
  * ✅ Delta / Arceus X / Codex (Android & iOS)
  * ✅ Fluxus / Vega X / KRNL
* **Fitur Cleanup:** Memanggil `_G.AdminSystemPanelCleanup()` untuk menghapus UI dan menghentikan semua background thread sebelum inject baru, mencegah lag/memory leak.

---

## 📁 Struktur File Proyek

```
RCU/
├── src/
│   ├── AdminPanel_aceu9922.lua   # Script utama panel otomatisasi (Tier 2)
│   ├── Loader.lua                # Gateway key system & loader (Tier 1)
│   ├── current_keys.txt          # Daftar kunci akses harian aktif
│   ├── check_syntax.js           # Tool verifikasi sintaks & batas lokal
│   └── README.md                 # Dokumentasi resmi sistem
```

---

<div align="center">
  <sub>Dibuat dengan ❤️ untuk komunitas RCU oleh <b>aceu9922</b></sub>
</div>
