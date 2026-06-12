---
title: "error: hd0 msdos1 read error"
date: 2011-04-01
forum: General Help
---

### Post by quanct on 2011-04-01
When booting up, I'm given an error message, "hd0,msdos1 read error" and a grub-rescue> prompt. I've run the boot info script in a LiveCD session, but I'm not sure how to interpret the results below. Where do I go from here?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   114,139,135   114,137,088  83 Linux
/dev/sda2         114,141,182   117,209,087     3,067,906   5 Extended
/dev/sda5         114,141,184   117,209,087     3,067,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16013852672 bytes
78 heads, 14 sectors/track, 28641 cylinders, total 31277056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    31,277,055    31,268,992   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       66720f0f-8aa7-481c-b5f7-3abfd69ea40f   ext3                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        af72a735-f79b-4f07-9d90-240b5402fa01   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        95fbb402-27bb-4bf0-890b-5959709f3af9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2939-23A3                              vfat       MUSHKIN                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  af 46 6d 77 8f be ef 7c  62 f4 6a 83 34 6c ea 95  |.Fmw...|b.j.4l..|
00000010  a6 a2 57 ff ff ff ff ff  ff ff ff ff ff ff ff ff  |..W.............|
00000020  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000000a0  ff ff ff ff ff ff ff ff  ff ff fc 92 9b 96 cd b6  |................|
000000b0  d6 c9 30 5c b1 33 0c 72  da 2b 7c d5 dd 36 f1 b3  |..0\.3.r.+|..6..|
000000c0  c3 48 6b 62 79 b1 57 32  58 58 30 36 15 9a 10 3e  |.Hkby.W2XX06...>|
000000d0  ba 30 36 7d 64 0d de 17  de 85 08 07 16 8b e3 58  |.06}d..........X|
000000e0  76 24 32 b7 19 d8 a0 75  7b 11 5f 09 15 72 99 ae  |v$2....u{._..r..|
000000f0  b2 db 6c 2d d0 ea d6 a1  74 75 28 a1 2d 52 34 17  |..l-....tu(.-R4.|
00000100  08 39 d5 18 17 0d b5 60  4a 31 55 75 2b 2a b5 c5  |.9.....`J1Uu+*..|
00000110  76 ba 4f c7 71 83 84 f0  d1 38 d7 86 aa 99 14 ed  |v.O.q....8......|
00000120  91 5c 95 a2 a1 8d cc fc  c3 32 25 bd be 03 c5 32  |.\.......2%....2|
00000130  b1 fd cf 83 c8 eb 7e 85  76 f6 05 04 0b b4 2d ae  |......~.v.....-.|
00000140  a6 c3 49 88 9c 5d c2 49  e8 bc ee 1e df a5 d2 2f  |..I..].I......./|
00000150  26 7b 99 27 68 87 46 17  35 93 b5 95 96 d0 5b 97  |&{.'h.F.5.....[.|
00000160  31 5c 63 24 10 ab b6 3c  84 b9 69 c4 68 6f 57 dc  |1\c$...<..i.hoW.|
00000170  13 d1 60 19 6e 2a e7 08  0d cd 32 dc 84 9b b7 6f  |..`.n*....2....o|
00000180  f6 fb 5b 70 ca b2 af 21  95 11 a5 88 97 d1 d4 8e  |..[p...!........|
00000190  65 b9 93 0e 8f bb 36 dd  82 96 e7 34 44 12 4d b5  |e.....6....4D.M.|
000001a0  1d 98 d6 3e 9a 9f b6 43  88 cb 66 47 2b 42 26 e9  |...>...C..fG+B&.|
000001b0  a4 89 f9 75 3c d1 ae fa  39 e5 12 2e ae 5f 00 fe  |...u<...9...._..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 2e 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 60 02  |.X.SYSLINUX..@`.|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 80 1f 00 00  |........?.......|
00000020  80 20 dd 01 f0 0e 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 08 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 a3 23 39 29 4d  55 53 48 4b 49 4e 20 20  |..).#9)MUSHKIN  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 80 f5 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

Also, here are the results of dmesg | tail, as suggested by the boot info results:

```
[ 2914.344733] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2914.344745] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 2914.344760] Descriptor sense data with sense descriptors (in hex):
[ 2914.344767]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2914.344799]         00 00 08 08 
[ 2914.344813] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2914.344832] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 00 08 08 00 00 08 00
[ 2914.344860] end_request: I/O error, dev sda, sector 2056
[ 2914.344873] Buffer I/O error on device sda1, logical block 1
[ 2914.344919] ata1: EH complete

```

---

### Post by quanct on 2011-04-01
.

---

### Post by quanct on 2011-04-01
bump

---

