# Laporan Resmi Tugas 1 Komunikasi Data dan Jaringan Komputer 

| No  | Nama                   | NRP        |
| --- | ---------------------- | ---------- |
| 1   | Kanafira Vanesha Putri | 5027241010 |

## Topology

Cisco Packet Tracer
<img width="1195" height="683" alt="image" src="https://github.com/user-attachments/assets/f3428283-74da-476f-8897-14c79782e4dd" />

## Base Network dan Subnetting

### Base Network Unik

```
NRP 5027241010 mod 256 = 50
Base = 10.50.0.0
```

### Subnetting
```
IP Prefix: 10.50.0.0/22
Total Host: 778 host
```

| **Nama Subnet**                    | **Host** | **Host + Gateway** | **Netmask** |
|-----------------------------------|---------:|--------------------:|:-----------:|
| Sekretariat                       |     380 |                381  | /23         |
| Bidang Kurikulum                  |     220 |                221  | /24         |
| Bidang Guru & Tendik              |      95 |                 96  | /25         |
| Bidang Sarana Prasarana           |      45 |                 46  | /26         |
| Bidang Pengawas Sekolah           |      18 |                 19  | /27         |
| Server & Admin                    |       6 |                  7  | /28         |
| Jaringan Gabungan                 |       6 |                  6  | /29         |
| Tunnel (Link Pusat dan Cabang)    |       2 |                  2  | /30         |
| TOTAL                             |         |              **778**| **/22**     |


# VLSM

## Topologi VLSM

<img width="1243" height="720" alt="Screenshot 2025-11-13 135757" src="https://github.com/user-attachments/assets/dd6fdd1a-2267-42c5-ae6a-65e51f541120" />


## Pohon VLSM

```
                                    10.50.0.0/22
                                         |
                        ┌────────────────┴────────────────┐
                        ↓                                 ↓
                  10.50.0.0/23                      10.50.2.0/23
                        ↓                                 ↓
               ┌────────┴────────┐               ┌────────┴────────┐
               ↓                 ↓               ↓                 ↓
         10.50.0.0/24      10.50.1.0/24    10.50.2.0/24      10.50.3.0/24
               ↓                            Bidang Kurikulum       ↓
       ┌───────┴───────┐                   10.50.2.0/24    ┌──────┴──────┐
       ↓               ↓                                    ↓             ↓
  10.50.0.0/25   10.50.0.128/25                      10.50.3.0/25  10.50.3.128/25
       ↓               ↓                              Bidang Guru        ↓
  ┌────┴────┐     ┌────┴────┐                        & Tendik      ┌────┴────┐
  ↓         ↓     ↓         ↓                        10.50.3.0/25  ↓         ↓
10.50.0   10.50.0 10.50.0  10.50.0                            10.50.3   10.50.3
.0/26     .64/26  .128/26  .192/26                            .128/26   .192/26
  ↓                   ↓                                        Bidang         ↓
10.50.0           10.50.0                                     Sarana    Bidang Pengw
.0/27             .128/27                                     Prasarana  Sekolah
  ↓                   ↓                                        10.50.3   10.50.3
10.50.0           10.50.0                                     .128/26   .192/27
.0/28             .128/28                                         ↓         ↓
  ↓                   ↓                                        10.50.3   10.50.3
10.50.0           10.50.0                                     .129-190  .193-222
.0/29             .128/29
  ↓                   ↓
10.50.0           10.50.0
.0/30             .8/29
  ↓                   ↓
Sekretariat      Server & Admin
10.50.0.0/23     10.50.3.224/29
                      ↓
                 Jaringan Backbone
                 10.50.3.232/29
                      ↓
                  Link WAN
                 10.50.3.240/30
```

## Perhitungan Subnetting VLSM 

| **Nama Subnet**                   | **Kebutuhan Host** | **Network Address** | **Prefix** | **Subnet Mask**       | **Host Range**                | **Broadcast Address** | **Gateway Address** |
|-----------------------------------|--------------------|----------------------|------------|----------------------|-------------------------------|------------------------|----------------------|
| Sekretariat                       | 381                | 10.50.0.0            | /23        | 255.255.254.0        | 10.50.0.1 - 10.50.1.254       | 10.50.1.255            | 10.50.0.1            |
| Bidang Kurikulum                  | 221                | 10.50.2.0            | /24        | 255.255.255.0        | 10.50.2.1 - 10.50.2.254       | 10.50.2.255            | 10.50.2.1            |
| Bidang Guru & Tendik              | 96                 | 10.50.3.0            | /25        | 255.255.255.128      | 10.50.3.1 - 10.50.3.126       | 10.50.3.127            | 10.50.3.1            |
| Bidang Sarana Prasarana           | 46                 | 10.50.3.128          | /26        | 255.255.255.192      | 10.50.3.129 - 10.50.3.190     | 10.50.3.191            | 10.50.3.129          |
| Bidang Pengawas Sekolah (Cabang)  | 19                 | 10.50.3.192          | /27        | 255.255.255.224      | 10.50.3.193 - 10.50.3.222     | 10.50.3.223            | 10.50.3.193          |
| Server & Admin                    | 7                  | 10.50.3.224          | /29        | 255.255.255.248      | 10.50.3.225 - 10.50.3.230     | 10.50.3.231            | 10.50.3.225          |
| Jaringan Gabungan                 | 6                  | 10.50.3.232          | /29        | 255.255.255.248      | 10.50.3.233 - 10.50.3.238     | 10.50.3.239            | 10.50.3.233          |
| Tunnel (Link Pusat dan Cabang)    | 2                  | 10.50.3.240          | /30        | 255.255.255.252      | 10.50.3.241 - 10.50.3.242     | 10.50.3.243            | 10.50.3.241          |

---

# CIDR


## Topologi CIDR

<img width="1177" height="697" alt="Screenshot 2025-11-13 135908" src="https://github.com/user-attachments/assets/8999a7be-ced7-40d2-85a0-0f46732dfa84" />


## Pohon CIDR

```
                                    C1 /21
                                10.54.0.0/21
                                      |
                     ┌────────────────┴────────────────┐
                     ↓                                 ↓
                  B1 /22                            B2 /26
              10.54.0.0/22                      10.54.4.0/26
                     ↓                                 ↓
            ┌────────┴────────┐                 ┌──────┴──────┐
            ↓                 ↓                 ↓             ↓
         A5 /23            A6 /29           A7 /27        A8 /30
      10.54.0.0         10.54.3.208      10.54.4.0    10.54.4.32/30
      Sekretariat    Jaringan Gabungan  Bidang Pengw   Tunnel (Link
                                         Sekolah        Pusat-Cabang)
            ↓
      ┌─────┴─────┐
      ↓           ↓
   A2 /24      A1 /25
  10.54.2.0   10.54.3.0
  Bidang      Bidang Guru
  Kurikulum   & Tendik
      ↓
   A3 /26
  10.54.3.128
  Bidang Sarana
  Prasarana
      ↓
   A4 /28
  10.54.3.192
  Server & Admin
```

**Proses Penggabungan CIDR (Base: 10.50.0.0):**

### Level A (Subnet Awal):
- **A1** = 10.50.3.0/25 (Bidang Guru & Tendik)
- **A2** = 10.50.2.0/24 (Bidang Kurikulum)
- **A3** = 10.50.3.128/26 (Bidang Sarana Prasarana)
- **A4** = 10.50.3.224/29 (Server & Admin)
- **A5** = 10.50.0.0/23 (Sekretariat)
- **A6** = 10.50.3.232/29 (Jaringan Gabungan)
- **A7** = 10.50.3.192/27 (Bidang Pengawas Sekolah)
- **A8** = 10.50.3.240/30 (Tunnel/Link WAN)

### Level B (Penggabungan Pertama):
- **B1** = A5 + A2 + A1 + A3 + A4 + A6 → 10.50.0.0/22
- **B2** = A7 + A8 → 10.50.3.192/26

### Level C (ROOT):
- **C1** = B1 + B2 → **10.50.0.0/21** 

## Perhitungan Subnetting CIDR

| **Subnet** | **Prefix (CIDR)** | **Description**                       | **Network Address** | **Subnet Mask**     | **Usable Host Range**         | **Broadcast Address** | **Suggested Gateway** |
|------------|-------------------|----------------------------------------|----------------------|---------------------|-------------------------------|------------------------|------------------------|
| A1         | /23               | Sekretariat                           | 10.50.0.0            | 255.255.254.0       | 10.50.0.1 - 10.50.1.254       | 10.50.1.255            | 10.50.0.1              |
| A2         | /24               | Bidang Kurikulum                      | 10.50.2.0            | 255.255.255.0       | 10.50.2.1 - 10.50.2.254       | 10.50.2.255            | 10.50.2.1              |
| A3         | /25               | Bidang Guru dan Tendik                | 10.50.3.0            | 255.255.255.128     | 10.50.3.1 - 10.50.3.126       | 10.50.3.127            | 10.50.3.1              |
| A4         | /26               | Bidang Sarana Prasarana               | 10.50.3.128          | 255.255.255.192     | 10.50.3.129 - 10.50.3.190     | 10.50.3.191            | 10.50.3.129            |
| A5         | /27               | Bidang Pengawas Sekolah (Cabang)      | 10.50.3.192          | 255.255.255.224     | 10.50.3.193 - 10.50.3.222     | 10.50.3.223            | 10.50.3.193            |
| A6         | /29               | Server dan Admin                      | 10.50.3.224          | 255.255.255.248     | 10.50.3.225 - 10.50.3.230     | 10.50.3.231            | 10.50.3.225            |
| A7         | /29               | Jaringan Gabungan / Backbone          | 10.50.3.232          | 255.255.255.248     | 10.50.3.233 - 10.50.3.238     | 10.50.3.239            | 10.50.3.233            |
| A8         | /30               | Tunnel (Link Pusat dan Cabang)        | 10.50.3.240          | 255.255.255.252     | 10.50.3.241 - 10.50.3.242     | 10.50.3.243            | 10.50.3.241            |
