---
title: "grub error on newly installed ubuntu 11.10"
date: 2011-10-14
forum: General Help
---

### Post by experience on 2011-10-14
When I finished fresh installation. I get an error of grub:

error: no such device: (my disk uuid)
grub rescue>

ls commmand:

grub rescue> ls
(hd0)

My disk is an Intel Raid, when it was working in Ubuntu 11.04 and LiveCD environment, it's named /dev/mapper/isw_blablabalp5.

I checked by using LiveCD, the UUID is correct.
I doesn't have problem using Ubuntu 11.04. And I have tried to upgrade from a working Ubuntu 11.04, it gets the same error.

What could be the error? How can I fix it?

Thanks!

Here is the output of boot info script
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_jdbdbhajd_RAID-0 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks in partition 256 for .

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
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>........).V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1457480 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdc1 starts at sector 
                       0. But according to the info from fdisk, sdc1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

isw_jdbdbhajd_RAID-01: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_jdbdbhajd_RAID-02: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_jdbdbhajd_RAID-03: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_jdbdbhajd_RAID-04: _________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_jdbdbhajd_RAID-05: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_jdbdbhajd_RAID-06: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/sdb1     ? 1,319,511,497 2,870,882,863 1,551,371,367  8f Unknown
/dev/sdb2     ? 1,817,928,266 5,646,432,751 3,828,504,486  91 Free FDISK hidden Extended
/dev/sdb3     ? 3,037,689,319 7,058,685,574 4,020,996,256  d2 Unknown
/dev/sdb4     ? 3,888,500,488 5,331,616,709 1,443,116,222  dc Unknown

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb2
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb2 overlaps with /dev/sdb3
/dev/sdb2 overlaps with /dev/sdb4
/dev/sdb3 ends after the last sector of /dev/sdb
/dev/sdb3 overlaps with /dev/sdb4
/dev/sdb4 ends after the last sector of /dev/sdb

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8010 MB, 8010194944 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15644912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62    15,635,593    15,635,532   c W95 FAT32 (LBA)


Drive: isw_jdbdbhajd_RAID-0 _____________________________________________________________________

Disk /dev/mapper/isw_jdbdbhajd_RAID-0: 1500.3 GB, 1500308045824 bytes
255 heads, 63 sectors/track, 182402 cylinders, total 2930289152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_jdbdbhajd_RAID-01   *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/mapper/isw_jdbdbhajd_RAID-02            409,600   419,842,709   419,433,110   7 NTFS / exFAT / HPFS
/dev/mapper/isw_jdbdbhajd_RAID-03        419,844,096   462,598,143    42,754,048   7 NTFS / exFAT / HPFS
/dev/mapper/isw_jdbdbhajd_RAID-04        462,598,270 2,930,287,615 2,467,689,346   5 Extended
/dev/mapper/isw_jdbdbhajd_RAID-05        462,598,272 2,914,279,807 2,451,681,536  83 Linux
/dev/mapper/isw_jdbdbhajd_RAID-06      2,914,279,936 2,930,287,615    16,007,680  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       9a53c973-577f-48c3-ad1d-919b89188b6b   ext3       
/dev/mapper/isw_jdbdbhajd_RAID-0p1 08F404F2F404E432                       ntfs       SYSTEM
/dev/mapper/isw_jdbdbhajd_RAID-0p2 1C3894103893E754                       ntfs       
/dev/mapper/isw_jdbdbhajd_RAID-0p3 44AAA91CAAA90C0C                       ntfs       RECOVERY
/dev/mapper/isw_jdbdbhajd_RAID-0p5 9a96979d-56e9-4085-8ec4-186355bdb1d3   ext4       
/dev/mapper/isw_jdbdbhajd_RAID-0p6 1f32e11f-8db3-4317-8568-b35ab5f1b9ab   swap       
/dev/sda                                                isw_raid_member 
/dev/sdc1        DAA0-A4DA                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_jdbdbhajd_RAID-0
isw_jdbdbhajd_RAID-0p1
isw_jdbdbhajd_RAID-0p2
isw_jdbdbhajd_RAID-0p3
isw_jdbdbhajd_RAID-0p5
isw_jdbdbhajd_RAID-0p6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_jdbdbhajd_RAID-0p5 /media/disk              ext4       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  0b 71 c1 b9 cb d2 b9 0d  36 db b9 33 0d 0f 0e cd  |.q......6..3....|
00000010  a3 c5 2c 7c 12 a0 f9 b7  7d 3c 33 80 f0 a6 ff 0f  |..,|....}<3.....|
00000020  40 6d cb 87 e4 57 5d 87  42 6a 48 12 19 50 a5 9c  |@m...W].BjH..P..|
00000030  87 25 1e b1 3e 2e 2f a0  ee b5 af de 0e 58 9b be  |.%..>./......X..|
00000040  a1 fe 2d e1 56 43 40 9c  77 4c f9 b7 db 08 22 25  |..-.VC@.wL...."%|
00000050  c1 bc 7c 95 f4 7e 24 bd  25 0c c9 5b b1 33 48 f8  |..|..~$.%..[.3H.|
00000060  86 0b f9 ae 3e e1 44 a8  e1 04 9a c2 66 24 c8 ce  |....>.D.....f$..|
00000070  57 78 61 4b 23 27 dc b6  8f 40 b0 6a 8f e7 f2 64  |WxaK#'...@.j...d|
00000080  16 f8 2e 59 5d a2 88 0d  9c 4a 34 26 32 1c 89 43  |...Y]....J4&2..C|
00000090  d9 1d f8 aa 32 a6 51 cc  ba 51 fe 11 08 d0 4f 96  |....2.Q..Q....O.|
000000a0  5f a9 73 ad 72 c8 f6 cd  7f 4c ef 4c 04 ad 17 d9  |_.s.r....L.L....|
000000b0  5c 15 a7 13 9f 85 a2 34  46 88 76 b5 d3 80 dd e0  |\......4F.v.....|
000000c0  87 6b 82 ca 7d f6 fe c4  35 f6 3b 4d 4f a3 a1 de  |.k..}...5.;MO...|
000000d0  2c e8 04 4f a8 ee bf 57  56 21 54 71 05 87 77 82  |,..O...WV!Tq..w.|
000000e0  cb da 53 4f a9 eb 7b 37  60 ac ba 23 c5 fa e8 91  |..SO..{7`..#....|
000000f0  b1 91 3c 72 a2 7d ad 2b  04 42 74 a5 5a c8 77 f2  |..<r.}.+.Bt.Z.w.|
00000100  98 d7 a4 a4 d8 4d da b8  45 40 35 56 45 08 bc a1  |.....M..E@5VE...|
00000110  be 51 c9 d2 b0 5c 19 81  ee 18 6b ce 83 a0 31 10  |.Q...\....k...1.|
00000120  63 03 ee a3 df a2 45 f4  c0 d1 ae 34 74 fa d7 49  |c.....E....4t..I|
00000130  15 b0 83 bf 32 39 de 48  13 89 b1 c2 9a 59 04 da  |....29.H.....Y..|
00000140  8a 24 db c9 8e f2 27 a2  65 fa 24 e0 a7 a6 89 42  |.$....'.e.$....B|
00000150  b5 18 92 69 f2 81 3a 30  b0 de 65 5f 39 b5 e6 1c  |...i..:0..e_9...|
00000160  e6 5e a5 1d a8 0a ec 80  5e 55 6a 11 d2 8c f5 85  |.^......^Uj.....|
00000170  da d9 87 71 e0 eb ee e7  57 4a 66 58 79 28 e5 81  |...q....WJfXy(..|
00000180  34 57 1e 2f 19 99 d1 e4  88 2e 08 56 a1 4e c9 46  |4W./.......V.N.F|
00000190  ee 32 c7 d1 1a 4c ac 10  d4 64 76 b0 07 88 c4 8c  |.2...L...dv.....|
000001a0  84 de 86 31 ed 83 ae 80  79 27 cd 6e c0 ee 8c 85  |...1....y'.n....|
000001b0  41 9f 4a c7 95 ea 1f ed  b7 4c ac c4 f0 4a b0 39  |A.J......L...J.9|
000001c0  36 6f 8f cd e1 30 c9 25  a6 4e 67 0c 78 5c a7 18  |6o...0.%.Ng.x\..|
000001d0  e1 f3 91 98 f9 d2 4a 62  5b 6c a6 57 32 e4 44 93  |......Jb[l.W2.D.|
000001e0  bc c9 d2 63 d9 80 e7 75  0f b5 a0 88 ab ef 51 7e  |...c...u......Q~|
000001f0  1e 86 dc 0b d2 83 08 cf  c5 e7 be 34 04 56 6a 0f  |...........4.Vj.|
00000200

Unknown BootLoader on sdb1


Unknown BootLoader on sdb2


Unknown BootLoader on sdb3


Unknown BootLoader on sdb4


Unknown BootLoader on isw_jdbdbhajd_RAID-01


Unknown BootLoader on isw_jdbdbhajd_RAID-02


Unknown BootLoader on isw_jdbdbhajd_RAID-03


Unknown BootLoader on isw_jdbdbhajd_RAID-04


Unknown BootLoader on isw_jdbdbhajd_RAID-05


Unknown BootLoader on isw_jdbdbhajd_RAID-06



=============================== StdErr Messages: ===============================

unlzma: Decoder error
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-01: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-01: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-02: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-02: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-03: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-03: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-04: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-04: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-05: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-05: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-06: No such file or directory
hexdump: /dev/mapper/isw_jdbdbhajd_RAID-06: No such file or directory

```

---

### Post by experience on 2011-10-14
Bump! Can anyone help?

---

### Post by effenberg0x0 on 2011-10-14
Have you tried the instructions posted here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards,
Effenberg

---

### Post by experience on 2011-10-14
Thanks for you reply! I haven't used this specific program. But I have tried to fix my grub using command line. I will try to use this tool. And post my results.

Thanks.

---

### Post by experience on 2011-10-14
> **effenberg0x0 said:**
> Have you tried the instructions posted here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards,
Effenberg

No, the recommended fix doesn't work.

Do you have any suggestion if I want to try advanced fix?

---

### Post by experience on 2011-10-14
I found a workaround, reinstall grub using LiveCD, with modified command, for my machine it's:

> sudo grub-install --modules="part_msdos" --root-directory=/media/disk /dev/dm-0

---

### Post by mardibloke on 2011-10-31
Could you give a little more detail on how you came up with your fix.

Also from LiveCD boot, what/if you had to mount, before issuing the command.

I have been trying RAID0 with two real SSD's. 11.10 Oneiric Alt install CD, all goes fine until I try and install GRUB.  The more I read about setting up partitions and installing grub the more confused I have become.

- --
Rod,  UK

---

