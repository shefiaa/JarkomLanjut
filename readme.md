Nama : Shefia Anggraeni
Nim : 20210801104
kode Matakuliah : 8126
Mata Kuliah : Jaringan Komputer Lanjut

# 1. Jelaskan menurut anda apa itu Routing Static? #

   Jawab : Routing Static Menurut saya, routing static metode routing di mana jalur jaringan ditentukan dan dikonfigurasi secara manual oleh administrator jaringan. Ini berarti setiap rute yang akan dilalui oleh paket data dari satu titik ke titik lain di dalam jaringan perlu diatur secara manual. Routing static biasanya diterapkan pada jaringan yang sederhana dan stabil, karena metode ini tidak dapat menyesuaikan diri secara otomatis jika ada perubahan pada topologi jaringan. 


# 2. Jelaskan menurut anda apa itu Routing Dynamic? #
   Jawab : Routing dynamic metode routing yang lebih canggih di mana rute antar perangkat jaringan dikelola secara otomatis menggunakan protokol routing seperti OSPF (Open Shortest Path First), RIP (Routing Information Protocol), atau EIGRP (Enhanced Interior Gateway Routing Protocol). 

# 3. Jelaskan menurut anda apa itu Firewall? #
   Jawab : Menurut saya, firewall komponen penting dalam keamanan jaringan yang berfungsi untuk mengontrol dan memantau lalu lintas jaringan berdasarkan aturan yang telah ditetapkan. Firewall berperan sebagai penghalang antara jaringan internal dan jaringan eksternal, serta berfungsi untuk melindungi jaringan internal dari ancaman seperti serangan siber, virus, dan akses tidak sah. 

# 4. Jelaskan menurut anda apa itu NAT?#
   Jawab : Menurut saya, NAT (Network Address Translation) teknologi yang memungkinkan beberapa perangkat di dalam jaringan lokal untuk menggunakan satu alamat IP publik saat berkomunikasi dengan internet. Dengan menggunakan NAT, alamat IP privat dari perangkat-perangkat di jaringan lokal dapat disembunyikan, dan mereka semua bisa mengakses internet dengan alamat IP publik yang sama. Menurut saya, NAT ini sangat berguna dalam menghemat penggunaan alamat IP publik, karena tidak semua perangkat membutuhkan alamat IP publik yang unik. 

# CASED #
![alt text](<Topologi Jarkom lanjut shefia.png>)

# Konfigurasi Jaringan Antar Kampus (KJ, CR, KHI)

## Deskripsi Proyek

Proyek ini adalah konfigurasi jaringan untuk menghubungkan tiga kampus (KJ, CR, KHI) menggunakan router dan switch. Setiap kampus memiliki router yang terhubung ke internet dan jaringan lokal. Kampus KJ bertindak sebagai pusat, dengan IPIP Tunnel menghubungkan masing-masing kampus, Komunikasi jaringan antar kampus.


## Topologi Jaringan

- **Router R1 (Kampus KJ)** - sebagai pusat jaringan
- **Router R2 (Kampus CR)**
- **Router R3 (Kampus KHI)**

## Detail Konfigurasi

### Router R1 (Kampus KJ sebagai pusat)

1. **Interface Ethernet 1**: Terhubung ke internet
   - IP: `10.10.10.1/30`

2. **Tunnel 1 (IPIP Tunnel)**: Menghubungkan R1 (KJ) dengan R2 (CR)
   - IP Tunnel: `16.16.16.1/30`

3. **Interface Ethernet 2**: Menghubungkan jaringan lokal di Kampus KJ
   - IP: `192.168.70.1/24`
   - Terhubung ke switch untuk mendistribusikan koneksi ke perangkat di jaringan internal Kampus KJ

### Router R2 (Kampus CR)

1. **Interface Ethernet 1**: Terhubung ke internet
   - IP: `10.10.10.2/30`

2. **Tunnel 1 (IPIP Tunnel)**: Menghubungkan R2 (CR) dengan R1 (KJ)
   - IP Tunnel: `16.16.16.2/30`

3. **Tunnel 2 (IPIP Tunnel)**: Menghubungkan R2 (CR) dengan R3 (KHI)
   - IP Tunnel: `17.17.17.1/30`

4. **Interface Ethernet 2**: Menghubungkan jaringan lokal di Kampus CR
   - IP: `192.168.80.1/24`
   - Terhubung ke switch untuk mendistribusikan koneksi ke perangkat di jaringan internal Kampus CR

### Router R3 (Kampus KHI)

1. **Interface Ethernet 1**: Terhubung ke internet
   - IP: `15.15.15.2/24`

2. **Tunnel 1 (IPIP Tunnel)**: Menghubungkan R3 (KHI) dengan R2 (CR)
   - IP Tunnel: `17.17.17.2/30`

3. **Interface Ethernet 2**: Menghubungkan jaringan lokal di Kampus KHI
   - IP: `192.168.90.1/24`
   - Terhubung ke switch untuk mendistribusikan koneksi ke perangkat di jaringan internal Kampus KHI


## Koneksi Antar Router

- **IPIP Tunnel** digunakan untuk menghubungkan router di masing-masing kampus melalui alamat IP tunnel. Tunnel ini memungkinkan setiap jaringan kampus untuk saling berkomunikasi melalui koneksi yang aman.
- **Tunnel 16.16.16.0/30** menghubungkan router KJ (R1) dan router CR (R2).
- **Tunnel 17.17.17.0/30** menghubungkan router CR (R2) dan router KHI (R3).


## Subnet Lokal

- **Kampus KJ**: `192.168.70.0/24`
- **Kampus CR**: `192.168.80.0/24`
- **Kampus KHI**: `192.168.90.0/24`

Setiap subnet ini dihubungkan melalui switch ke perangkat-perangkat di masing-masing kampus.




