---
title: "Formatted bootloader and windows partition"
date: 2011-06-24
forum: General Help
---

### Post by neo1786 on 2011-06-24
Hi, This might be the weirdest post u have come across.

I had a Windows 7 & Ubuntu 10.04 dual boot, installed from a Live CD,not using Wubi.

i was running a script to format a sd card. the script assumed the sd card to be on sdb while actually my 500GB hard drive was on sdb.

now i cant boot any OS, obviously! and get stuck at a grub rescue prompt. i want to kno if any data is recoverable. Also would it be possible ,somehow to get to the windows recovery partition?? here is my boot info script, if it is any help.
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     1,463,633     1,463,572  83 Linux
/dev/sdb2           1,463,634     2,927,267     1,463,634  83 Linux
/dev/sdb3           2,927,268     3,861,421       934,154  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  12 91 f2 60 90 a0 2f 19  01 00 00 00 85 00 67 68  |...`../.......gh|
00000010  46 50 3c a3 c4 4a ce 9f  c4 4a 32 00 ff ff 50 ed  |FP<..J...J2...P.|
00000020  12 00 18 ee 12 00 d6 7a  7c 00 ff ff ff ff 24 ee  |.......z|.....$.|
00000030  12 00 02 27 43 00 06 e8  c1 36 28 0a 00 00 02 00  |...'C....6(.....|
00000040  00 00 49 aa 80 7c 80 ee  12 00 00 ee 12 00 84 ee  |..I..|..........|
00000050  12 00 2a 7b 7c 00 ff 00  00 00 00 00 00 00 00 00  |..*{|...........|
00000060  00 00 00 00 00 00 00 00  00 00 00 57 44 43 20 57  |...........WDC W|
00000070  44 32 35 20 30 30 42 45  56 54 2d 32 36 5a 43 54  |D25 00BEVT-26ZCT|
00000080  30 20 31 32 2e 30 00 00  00 00 00 00 00 00 00 00  |0 12.0..........|
00000090  00 00 00 00 00 00 00 04  00 34 24 cc 9c 1f 00 00  |.........4$.....|
000000a0  28 1f 00 00 29 1f 00 00  2a 1f 00 00 2b 1f 00 00  |(...)...*...+...|
000000b0  2c 1f 00 00 2d 1f 00 00  2e 1f 00 00 2f 1f 00 00  |,...-......./...|
000000c0  30 1f 00 00 31 1f 00 00  32 1f 00 00 33 1f 00 00  |0...1...2...3...|
000000d0  34 1f 00 00 35 1f 00 00  36 1f 00 00 37 1f 00 00  |4...5...6...7...|
000000e0  38 1f 00 00 39 1f 00 00  3a 1f 00 00 3b 1f 00 00  |8...9...:...;...|
000000f0  3c 1f 00 00 3d 1f 00 00  3e 1f 00 00 3f 1f 00 00  |<...=...>...?...|
00000100  40 1f 00 00 41 1f 00 00  42 1f 00 00 43 1f 00 00  |@...A...B...C...|
00000110  44 1f 00 00 45 1f 00 00  46 1f 00 00 47 1f 00 00  |D...E...F...G...|
00000120  48 1f 00 00 49 1f 00 00  4a 1f 00 00 4b 1f 00 00  |H...I...J...K...|
00000130  4c 1f 00 00 4d 1f 00 00  4e 1f 00 00 4f 1f 00 00  |L...M...N...O...|
00000140  50 1f 00 00 51 1f 00 00  52 1f 00 00 53 1f 00 00  |P...Q...R...S...|
00000150  54 1f 00 00 55 1f 00 00  56 1f 00 00 57 1f 00 00  |T...U...V...W...|
00000160  58 1f 00 00 59 1f 00 00  5a 1f 00 00 5b 1f 00 00  |X...Y...Z...[...|
00000170  5c 1f 00 00 5d 1f 00 00  5e 1f 00 00 5f 1f 00 00  |\...]...^..._...|
00000180  60 1f 00 00 61 1f 00 00  62 1f 00 00 63 1f 00 00  |`...a...b...c...|
00000190  64 1f 00 00 65 1f 00 00  66 1f 00 00 67 1f 00 00  |d...e...f...g...|
000001a0  68 1f 00 00 69 1f 00 00  6a 1f 00 00 6b 1f 00 00  |h...i...j...k...|
000001b0  6c 1f 00 00 6d 1f 00 00  6e 1f 00 00 6f 1f 00 00  |l...m...n...o...|
000001c0  70 1f 00 00 71 1f 00 00  72 1f 00 00 73 1f 00 00  |p...q...r...s...|
000001d0  74 1f 00 00 75 1f 00 00  76 1f 00 00 77 1f 00 00  |t...u...v...w...|
000001e0  78 1f 00 00 79 1f 00 00  7a 1f 00 00 7b 1f 00 00  |x...y...z...{...|
000001f0  7c 1f 00 00 7d 1f 00 00  7e 1f 00 00 7f 1f 00 00  ||...}...~.......|
00000200

Unknown BootLoader on sdb2

00000000  8f ef 8c b7 23 8d f6 9d  da 9a 1a f8 47 87 2b 2e  |....#.......G.+.|
00000010  07 a0 7f 34 bb 5e e6 e2  22 e2 6c 0e c7 70 96 5e  |...4.^..".l..p.^|
00000020  98 e7 f6 2f 5e b4 9a ee  cf da b4 97 48 bd 23 7f  |.../^.......H.#.|
00000030  49 a0 79 90 de 16 23 10  07 4f df 7d 1c fd 55 8c  |I.y...#..O.}..U.|
00000040  22 0a 86 8e 8e 9a 8d eb  f6 f4 47 b4 c3 44 df 4e  |".........G..D.N|
00000050  79 54 d1 f4 1e 0b 0a 9f  1b 7c 30 47 2f cc 94 31  |yT.......|0G/..1|
00000060  93 cb 56 1b 53 66 25 3a  fc 78 df af 04 0a 5f 21  |..V.Sf%:.x...._!|
00000070  28 6a b6 38 f2 a3 73 3a  52 dc 6c 5b d3 83 39 c6  |(j.8..s:R.l[..9.|
00000080  94 92 b2 e7 23 cb 56 b7  a7 79 4f ba 9c 8b 08 56  |....#.V..yO....V|
00000090  8c 7b a8 2e 91 3e 25 93  c6 32 aa 2f 5c 46 86 0d  |.{...>%..2./\F..|
000000a0  ea 27 93 92 79 f8 f0 a1  65 54 6f 3c cf 6d fe 19  |.'..y...eTo<.m..|
000000b0  fc 48 03 91 88 67 98 ae  b7 b4 8d 09 2e ca 1e 4e  |.H...g.........N|
000000c0  53 96 6c 53 72 78 54 54  15 9e 83 2b e0 39 89 e7  |S.lSrxTT...+.9..|
000000d0  e0 f2 4c 54 e0 78 30 c8  3e 8c 75 f6 7c c0 33 41  |..LT.x0.>.u.|.3A|
000000e0  f4 d3 66 24 8a 15 7b 36  0e 67 5d fb dc f9 67 e8  |..f$..{6.g]...g.|
000000f0  3b 4c b1 7c 4a 50 1d 4d  f3 e6 37 47 ba 41 6f ee  |;L.|JP.M..7G.Ao.|
00000100  dc 79 99 a8 6f 14 d3 15  62 81 cf cb 9c fb 89 4d  |.y..o...b......M|
00000110  94 1f 3e b0 dd 6a 04 bd  e7 0a af 07 a3 69 7e 15  |..>..j.......i~.|
00000120  5f 56 96 2f 23 bc 82 1a  43 01 af bb f4 f3 6e d0  |_V./#...C.....n.|
00000130  3b e5 8b 78 db 45 7a e1  aa 92 80 18 f8 c4 d9 41  |;..x.Ez........A|
00000140  4f 07 3d 87 c6 88 2c 93  b3 6b b8 22 5c 1c c2 a3  |O.=...,..k."\...|
00000150  1e a3 17 f0 85 b6 d1 ad  80 3e 71 d0 0f 38 b4 f7  |.........>q..8..|
00000160  17 cd 9c 5d 24 aa ea 31  4e 0e 0f 7a 38 f9 84 96  |...]$..1N..z8...|
00000170  ed 42 f0 a7 29 9f af 9d  b3 7b 88 04 7c bc 97 d1  |.B..)....{..|...|
00000180  29 97 17 f8 63 c6 87 5b  01 a3 5a c5 c9 38 cf 3b  |)...c..[..Z..8.;|
00000190  dc f5 4d e0 96 66 b6 06  fc f2 87 39 5f 9a e4 e4  |..M..f.....9_...|
000001a0  a0 8a d1 5b 80 cd de eb  f6 7b fc b2 95 3b 59 4e  |...[.....{...;YN|
000001b0  ce 09 46 ce e0 ef 7c ad  bf e1 e2 2e da 22 6d 11  |..F...|......"m.|
000001c0  40 66 3c 34 ce cd df f8  a7 9f 70 7e 6b 03 7d 64  |@f<4......p~k.}d|
000001d0  84 0f b0 ac 1f b0 ab e1  f0 12 cc 27 c3 c7 32 90  |...........'..2.|
000001e0  ff a2 6a f5 53 9c 7c d9  55 27 c6 ef c6 66 7d 10  |..j.S.|.U'...f}.|
000001f0  fe 44 f9 5d f5 0f 21 af  28 d6 ad 93 df 3d 0f ca  |.D.]..!.(....=..|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sda 




```

---

### Post by neo1786 on 2011-06-24
I posted this again by mistake....
link to original

[http://ubuntuforums.org/showthread.php?t=1790108](http://ubuntuforums.org/showthread.php?t=1790108)

---

