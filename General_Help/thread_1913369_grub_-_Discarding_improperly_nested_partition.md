---
title: "grub - Discarding improperly nested partition"
date: 2012-01-22
forum: General Help
---

### Post by slemke on 2012-01-22
Hello @all,
 
I have a grub problem and have no idea what to do!?
 
In the System are 4x 2 TB HDDs used as an Raid5.
 
As found in another post I have already tried to re-create the swap partition without success.
 
First the error - followed by the output of boot info:
 
```
root@srvbck:/boot/grub# update-grub
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
Generating grub.cfg ...
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
Found linux image: /boot/vmlinuz-3.0.0-15-server
Found initrd image: /boot/initrd.img-3.0.0-15-server
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
Found linux image: /boot/vmlinuz-3.0.0-14-server
Found initrd image: /boot/initrd.img-3.0.0-14-server
Found linux image: /boot/vmlinuz-3.0.0-12-server
Found initrd image: /boot/initrd.img-3.0.0-12-server
Found linux image: /boot/vmlinuz-2.6.32-37-server
Found initrd image: /boot/initrd.img-2.6.32-37-server
Found linux image: /boot/vmlinuz-2.6.32-33-server
Found initrd image: /boot/initrd.img-2.6.32-33-server
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
/usr/sbin/grub-probe: warn: Discarding improperly nested partition (hd0,gpt2,gpt4).
Found memtest86+ image: /memtest86+.bin
done

```
 
 
```
                  Boot Info Script 0.60    from 17 May 2011
 
============================= Boot Info Summary: ===============================
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for  on this drive.
sda1: __________________________________________________________________________
    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  
sda2: __________________________________________________________________________
    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  
sdb1: __________________________________________________________________________
    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  
sdb2: __________________________________________________________________________
    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  
sdc1: __________________________________________________________________________
    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  
sdc2: __________________________________________________________________________
    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  
sdd1: __________________________________________________________________________
    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  
sdd2: __________________________________________________________________________
    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  
md0: ___________________________________________________________________________
    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT
 
GUID Partition Table detected.
Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048        20,479        18,432 BIOS Boot partition
/dev/sda2          20,480 3,907,028,991 3,907,008,512 RAID partition (Linux)
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT
 
GUID Partition Table detected.
Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048        20,479        18,432 BIOS Boot partition
/dev/sdb2          20,480 3,907,028,991 3,907,008,512 RAID partition (Linux)
Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdc1                   1 3,907,029,167 3,907,029,167  ee GPT
 
GUID Partition Table detected.
Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1           2,048        20,479        18,432 BIOS Boot partition
/dev/sdc2          20,480 3,907,028,991 3,907,008,512 RAID partition (Linux)
Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdd1                   1 3,907,029,167 3,907,029,167  ee GPT
 
GUID Partition Table detected.
Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1           2,048        20,479        18,432 BIOS Boot partition
/dev/sdd2          20,480 3,907,028,991 3,907,008,512 RAID partition (Linux)
"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/md0p1       4d377ecd-4d50-4a46-a836-a70eba197f1e   ext2       
/dev/md0p2       d7652bab-a7eb-408d-ab76-346b89ba6642   swap       
/dev/md0p3       a5bf88f4-7fd6-44e9-b26c-df5de3557367   ext3       
/dev/sda2        29f4d413-cd41-8b6c-1b42-652cd5f32cbd   linux_raid_member 
/dev/sdb2        29f4d413-cd41-8b6c-1b42-652cd5f32cbd   linux_raid_member 
/dev/sdc2        29f4d413-cd41-8b6c-1b42-652cd5f32cbd   linux_raid_member 
/dev/sdd2        29f4d413-cd41-8b6c-1b42-652cd5f32cbd   linux_raid_member 
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/md0p1       /boot                    ext2       (rw)
/dev/md0p3       /                        ext3       (rw,errors=remount-ro)
 
======================== Unknown MBRs/Boot Sectors/etc: ========================
Unknown BootLoader on sdb2
00000000  cb 49 5a da 8d 5b 76 dd  32 9b f4 4f 43 33 95 26  |.IZ..[v.2..OC3.&|
00000010  4b 8f 39 6d ba 1d 53 ce  ec b0 e3 f5 6d 86 9b 4a  |K.9m..S.....m..J|
00000020  68 a4 ab d2 ee 7a 56 6e  f6 10 e9 a5 c9 3a d4 6d  |h....zVn.....:.m|
00000030  17 d1 ee a8 78 3b 0a e9  fa a4 78 4a 5b 3a e6 28  |....x;....xJ[:.(|
00000040  a5 51 bd 5d 4b 27 5c a5  4e a9 28 53 2a e7 2d ec  |.Q.]K'\.N.(S*.-.|
00000050  58 42 9a 59 97 e2 da 9a  e9 b4 93 32 12 de 55 59  |XB.Y.......2..UY|
00000060  a6 54 d5 28 6d dd a4 c5  19 e6 15 69 c3 ee 66 78  |.T.(m......i..fx|
00000070  5e 99 e2 74 18 29 d6 6d  c9 b8 10 d3 95 85 8c 57  |^..t.).m.......W|
00000080  97 29 ed 46 97 12 d1 52  5a c4 70 3d d9 85 65 c4  |.).F...RZ.p=..e.|
00000090  6c 42 eb ce 52 50 49 4c  3a a4 5d a5 ac 4e 62 89  |lB..RPIL:.]..Nb.|
000000a0  b4 85 a8 41 3d 44 2b 86  34 52 db 25 ff 5a 29 32  |...A=D+.4R.%.Z)2|
000000b0  b0 1a ae 67 8f 88 53 bf  d9 46 94 16 84 8c 41 a6  |...g..S..F....A.|
000000c0  96 50 da 12 5a a4 83 8e  63 a0 92 0a d9 8a 46 bb  |.P..Z...c.....F.|
000000d0  6d 9b 61 6a 54 e1 1c e6  0f b7 3b a5 67 f9 84 a8  |m.ajT.....;.g...|
000000e0  08 70 9d ef 3f e1 a4 b5  a8 91 ef fb cd 8d b6 29  |.p..?..........)|
000000f0  ee 4f e4 ca 4b ca 94 34  19 74 57 b2 91 8f 1c 57  |.O..K..4.tW....W|
00000100  24 6d db b4 d7 1a e4 50  0c cd b5 6c 67 4e ae 3d  |$m.....P...lgN.=|
00000110  56 3e d1 66 9b 65 25 02  ca e7 d8 11 7a 12 a1 cd  |V>.f.e%.....z...|
00000120  a9 76 49 43 75 55 55 ed  92 ea ca 86 ea 86 f9 35  |.vICuUU........5|
00000130  35 55 35 0b 6b ce 59 52  11 90 09 b7 af 84 a1 39  |5U5.k.YR.......9|
00000140  75 fc 7c ba 68 83 6e 9e  96 b4 4e 73 52 34 02 bf  |u.|.h.n...NsR4..|
00000150  a6 a2 b6 91 28 67 61 fb  d5 0b ab 4e f3 da 6f 4a  |....(ga....N..oJ|
00000160  27 2e ab cb 04 da 47 2c  5b 1f 44 3f c9 9f d4 62  |'.....G,[.D?...b|
00000170  46 a4 4e 0c e1 57 5a 57  b4 d0 06 a3 a6 cd 84 a5  |F.N..WZW........|
00000180  45 e9 4f 38 10 47 41 f9  ef c9 73 ba 91 af dc ff  |E.O8.GA...s.....|
00000190  b7 74 e4 84 49 ec 09 1c  ef 49 0a 95 74 3c 72 ae  |.t..I....I..t<r.|
000001a0  19 46 fe 99 27 be cf 9e  2c 6f ef 54 23 8e ad 92  |.F..'...,o.T#...|
000001b0  73 8d 4d 9b ad 6a ea 5d  79 a9 79 ea ea 0d 97 41  |s.M..j.]y.y....A|
000001c0  7e af 77 a8 ba a9 b5 91  92 a4 e2 dd 8e 4a 4e d3  |~.w..........JN.|
000001d0  43 e4 5f d1 b1 96 bd f9  b1 23 c9 ce aa 6a 44 8b  |C._......#...jD.|
000001e0  c4 75 27 ff f2 7f b1 e9  1e f6 2a 8c a4 93 d0 f5  |.u'.......*.....|
000001f0  d4 50 d2 b9 e9 9d 05 f7  bf c6 ec db 7a bb 9a 1a  |.P..........z...|
00000200
Unknown BootLoader on sdc2
00000000  6c 07 6f bf 07 34 c7 d7  d2 3d c4 04 b6 83 a7 ff  |l.o..4...=......|
00000010  23 5d fa e9 39 21 2f 94  df 10 87 f4 1f d6 f8 0f  |#]..9!/.........|
00000020  d3 c5 74 65 1f 3b f7 30  3b f9 85 1c 79 3c 7f 24  |..te.;.0;...y<.$|
00000030  3a 85 6e 44 15 b0 1d fc  f8 a8 28 e7 f4 37 f7 35  |:.nD......(..7.5|
00000040  d3 5f 10 6b a5 7f 98 43  fa fb 6b fc 87 03 e4 9f  |._.k...C..k.....|
00000050  65 8c fb ef a3 f1 ef 1d  60 fa 4f 72 59 fe 8f 73  |e.......`.OrY..s|
00000060  f0 7f 7a 94 c9 22 f2 4f  37 cc ea 18 e7 fe 93 28  |..z..".O7......(|
00000070  fd 3c 0d 29 9a 1b 6e bc  fe a4 d0 f1 49 9c d3 f1  |.<.)..n.....I...|
00000080  93 d8 01 3c 7e c9 36 e5  f4 38 bb 9f ee 65 a4 6b  |...<~.6..8...e.k|
00000090  8e c7 ed 88 d8 21 96 ca  2a 73 1d a6 0e 6c b4 f8  |.....!..*s...l..|
000000a0  f7 b8 2b b2 fc 7a 6a fc  a7 fc ce 5c 17 0d 6f df  |..+..zj....\..o.|
000000b0  7f 7b 4b 8c 63 ca 24 e7  ad 48 f1 3e 1a de 57 c3  |.{K.c.$..H.>..W.|
000000c0  07 6b f8 30 0d 1f 19 c1  cc f2 b3 d2 d9 9b d6 03  |.k.0............|
000000d0  88 ab 78 a9 52 30 9a b8  87 f1 09 c4 55 3d 50 3a  |..x.R0......U=P:|
000000e0  33 88 a7 30 9e 49 3c 8b  f1 05 c4 b3 99 7e 2e f1  |3..0.I<......~..|
000000f0  32 c6 8b 8d 3c 0c 6b 4b  a7 5a 9b fd aa 95 5f 55  |2...<.kK.Z...._U|
00000100  bf 6f 22 9d 30 c5 a5 06  e2 b7 93 7d 2c b3 5f 43  |.o".0......},._C|
00000110  fa 2a bf 6a fd 27 e2 aa  42 28 bf 1b 89 ab fc 86  |.*.j.'..B(......|
00000120  69 bd 5d a5 93 d9 ef 65  7e d5 f2 ae c1 ad de 4a  |i.]....e~......J|
00000130  d5 8c 83 06 ef df c6 95  45 4f a3 1d 5a f5 41 dd  |........EO..Z.A.|
00000140  d7 3b c5 e0 03 db b8 aa  79 69 51 a6 0e 2f b7 1c  |.;......yiQ../..|
00000150  d2 51 c7 0f a0 f5 b5 a4  13 c7 74 ee 25 1d 0f d3  |.Q........t.%...|
00000160  59 4f 3a 27 b3 f4 bc 45  3a f1 4c e7 1b d2 49 62  |YO:'...E:.L...Ib|
00000170  3a fd a2 4d 9d 33 69 5b  e5 fc d4 68 53 27 81 e9  |:..M.3i[...hS'..|
00000180  cc 8a 36 75 52 98 8e 8f  74 2e 60 3a 57 93 8e 87  |..6uR...t.`:W...|
00000190  e9 dc 45 3a 59 4c 67 03  e9 2c a4 6d 15 1e 3e 20  |..E:YLg..,.m..> |
000001a0  9d 31 4c 27 2a c6 d4 c9  66 3a 27 c6 98 3a cb 69  |.1L'*...f:'..:.i|
000001b0  5b e5 23 2d c6 d4 49 62  3a 4b 49 a7 8c e9 84 48  |[.#-..Ib:KI....H|
000001c0  e7 56 96 9e 67 49 67 1a  d3 79 93 74 2a 99 ce 77  |.V..gIg..y.t*..w|
000001d0  a4 b3 96 a5 67 68 ac a9  93 c2 74 a6 c7 9a 3a b5  |....gh....t...:.|
000001e0  4c e7 92 58 53 27 4c db  ea bc 07 48 c7 cb 74 7e  |L..XS'L....H..t~|
000001f0  4b 3a 6b 98 ce f3 a4 f3  17 da 1e a2 d2 4f 3a 59  |K:k..........O:Y|
00000200
Unknown BootLoader on sdd2
00000000  a7 4e 35 65 8a 6f b1 0a  e0 a6 30 4b f5 b0 32 d9  |.N5e.o....0K..2.|
00000010  68 d2 c3 84 83 3c 7c 5a  33 a0 64 01 72 50 63 45  |h....<|Z3.d.rPcE|
00000020  bb 61 df b7 f1 41 a1 5e  cd e9 6c b9 b0 06 ab 49  |.a...A.^..l....I|
00000030  2d 54 80 ec 6d 8b 17 15  02 0c 50 ad af 0d 11 1d  |-T..m.....P.....|
00000040  76 0e ad 36 ee 58 c4 e6  b4 52 43 af ad e4 c9 73  |v..6.X...RC....s|
00000050  3d ce 61 b6 34 13 35 87  89 4e dc 40 4b 20 da 2a  |=.a.4.5..N.@K .*|
00000060  56 2b af bc a4 ff 56 8a  2e 2a ff 71 24 10 f5 50  |V+....V..*.q$..P|
00000070  a3 a5 ef 5d 82 32 b8 d1  37 1c c0 22 dc 19 5f a6  |...].2..7..".._.|
00000080  04 f1 ec 7a e9 db e7 b7  ae fc cb a2 37 e0 c1 af  |...z........7...|
00000090  e2 85 06 46 8a 71 df 86  10 d7 40 03 a2 22 d6 71  |...F.q....@..".q|
000000a0  43 3d 83 f3 c1 3e 41 7a  93 ae 15 79 e8 57 46 ed  |C=...>Az...y.WF.|
000000b0  cf 61 e5 eb ec 42 77 58  74 0e 65 28 9e 52 16 65  |.a...BwXt.e(.R.e|
000000c0  91 3b 22 22 57 bb 9a 4f  af 52 21 d8 00 11 90 b8  |.;""W..O.R!.....|
000000d0  e5 30 19 c3 06 d1 86 5e  88 46 32 61 32 c4 d4 92  |.0.....^.F2a2...|
000000e0  3b f8 3a df a1 a8 98 3e  59 94 2b 48 54 f3 98 d8  |;.:....>Y.+HT...|
000000f0  dc 89 6f 47 77 c6 ff 7f  be 2e cc 4f 3b 1a 43 02  |..oGw......O;.C.|
00000100  9b 02 f9 29 e7 df 41 56  ee 7a 26 11 4b fd f1 7e  |...)..AV.z&.K..~|
00000110  ac 14 6e 0c 66 42 c7 a8  88 cf 67 0a f3 b9 5d 4b  |..n.fB....g...]K|
00000120  c0 cb 14 e6 e6 8c ba 88  ec 3f 38 28 2b 2b 27 7f  |.........?8(++'.|
00000130  e0 d9 b6 0d 84 11 9f c7  54 df aa aa f5 71 e0 e4  |........T....q..|
00000140  a2 c7 b9 5a 6b 58 d6 34  ef dd 1f d5 5c 1b b5 a3  |...ZkX.4....\...|
00000150  74 f3 71 9e 88 92 d4 5f  c6 cc df a0 d6 c7 60 99  |t.q...._......`.|
00000160  7e 61 91 ec b7 2e fb 69  61 ee 08 d8 d2 4d 9d 00  |~a.....ia....M..|
00000170  7c 59 ec 41 7c 64 33 0c  51 2c d2 cb f5 ea 05 4c  ||Y.A|d3.Q,.....L|
00000180  89 63 79 4d 42 df cf 76  9b e7 13 80 c6 3c 52 78  |.cyMB..v.....<Rx|
00000190  5e a8 a1 be 10 a0 6e 1f  06 65 ae f8 61 22 4c 8e  |^.....n..e..a"L.|
000001a0  84 77 b2 be 0d 78 1b 57  4a 55 c8 92 bb b4 66 fb  |.w...x.WJU....f.|
000001b0  28 68 6e b6 6b be a3 3f  43 e2 30 4d 66 e4 13 09  |(hn.k..?C.0Mf...|
000001c0  98 f9 0f c8 22 1f d3 8b  41 dd 8e 56 5b 2c 80 a4  |...."...A..V[,..|
000001d0  e7 57 c9 74 d6 fe 11 50  22 e1 bd 68 6d f0 7e 3e  |.W.t...P"..hm.~>|
000001e0  88 92 b5 a7 a1 58 fd 32  f4 4a 2d c4 63 58 a4 8b  |.....X.2.J-.cX..|
000001f0  9f 6a b9 21 27 6e a1 04  a8 1c f2 79 a8 f4 f5 e9  |.j.!'n.....y....|
00000200
 
=============================== StdErr Messages: ===============================
unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error

```
 
 
```
root@srvbck:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd2[3] sda2[0] sdc2[2] sdb2[1]
      5860512576 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
unused devices: <none>

```
 
Thanks,
Sebastian

---

### Post by slemke on 2012-01-27
*push*

Nobody an idea ?

Are any additional Infos needed ?

I would like to bring the server in action, but without solving this issue I will not do it....

Thanks,
Sebastian

---

