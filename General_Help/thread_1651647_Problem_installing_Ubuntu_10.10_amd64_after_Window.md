---
title: "Problem installing Ubuntu 10.10 amd64 after Windows 7"
date: 2010-12-23
forum: General Help
---

### Post by baster8 on 2010-12-23
Hi, all

I have windows 7 64 bit installed. I used the universal-installer to put  Ubuntu 10.10 (64bit version) on my USB. I have partitioned my hard  drive into 4 partitions. First partition for windows 7 system reserve.  Second partition C for the main part of windows 7. The third partition  is logical and it is for random stuff. The fourth I intend to install  Ubuntu on it. I tried to left this fourth partition unallocated, format  it into ext3, format it into NTFS, but in any case, the Ubuntu installer  can not detect that I already have another OS on my HD, and when I go  into that "special partition option", Ubuntu installer only let me  repartition anything. It can't see the existing partitions. Below is the  result of the bootscript.

```

              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   148,440,599   148,233,752   7 HPFS/NTFS
/dev/sda3         148,438,615   518,883,434   370,444,820   f W95 Ext d (LBA)
/dev/sda5         148,440,663   518,883,434   370,442,772   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders, total 7905279 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,905,278     7,905,247   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C6F4EFD9F4EFCA2F                       ntfs       System Reserved               
/dev/sda2        01CBA280DB2F12C0                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        01CBA2813BEED5A0                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8A76-EFC0                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================


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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  b8 e4 dd 55 55 55 55 55  55 55 55 55 55 55 55 55  |...UUUUUUUUUUUUU|
00000010  55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  |UUUUUUUUUUUUUUUU|
*
00000030  55 55 55 55 55 55 55 55  55 55 55 55 55 55 00 02  |UUUUUUUUUUUUUU..|
00000040  00 1c c4 88 3d 8d 14 cc  80 fb a1 04 60 36 32 08  |....=.......`62.|
00000050  90 30 e0 34 1d 1b 0c 04  0c 8f 08 9e 4c 3e 2f cc  |.0.4........L>/.|
00000060  37 0e 4c 4c 10 8e 01 70  8d 3c 0b c1 44 79 89 c2  |7.LL...p.<..Dy..|
00000070  e1 b4 fc 41 cc 09 01 b2  4e 01 4f 0c 46 1c fb cd  |...A....N.O.F...|
00000080  cc 6d 10 8a c5 6c 9a f1  48 d0 fb 0f 69 c0 c1 04  |.m...l..H...i...|
00000090  ae 4f 75 1c 11 02 3d cd  5e 92 20 68 a6 a6 30 0e  |.Ou...=.^. h..0.|
000000a0  61 a0 04 04 26 7a 2c 69  66 a1 c4 06 24 36 6d 87  |a...&z,if...$6m.|
000000b0  81 02 8a fd ad 0a 18 16  07 0c b4 0c c5 08 cd 2b  |...............+|
000000c0  94 fb 57 cc 64 40 02 12  61 e1 23 cc d0 dd 22 db  |..W.d@..a.#...".|
000000d0  14 03 7b 5e cf a5 7b e2  9b 83 70 b5 51 3f 60 78  |..{^..{...p.Q?`x|
000000e0  1a fc ad 26 18 e6 d2 38  cc c8 cc 1c 0b 0b 4f e4  |...&...8......O.|
000000f0  46 08 99 83 69 21 a9 73  02 47 b5 87 8d a5 48 f1  |F...i!.s.G....H.|
00000100  24 71 6e 0c 81 99 30 93  e4 b8 5e 04 07 29 0b 4f  |$qn...0...^..).O|
00000110  93 d5 0f 3b ad 22 1b 42  08 e0 b0 0c 4e 2f 07 36  |...;.".B....N/.6|
00000120  b1 b0 b0 ca 83 3c 6f 21  00 5c e4 52 50 ac b2 f8  |.....<o!.\.RP...|
00000130  02 14 fb 2e 29 e9 54 06  f9 59 c7 3b 75 79 f4 dd  |....).T..Y.;uy..|
00000140  de 5b b5 6f 29 73 df 2e  c6 19 5c ad 8e e4 3e 9a  |.[.o)s....\...>.|
00000150  2d 7e 89 0d 0c 2c 01 5e  28 cc 3a b2 91 2e db 7f  |-~...,.^(.:.....|
00000160  3f 20 86 1b 35 b6 45 94  d5 78 62 92 82 d4 4e 8e  |? ..5.E..xb...N.|
00000170  d5 4a 98 67 13 ba fa cb  34 f3 48 a6 29 7d e5 45  |.J.g....4.H.)}.E|
00000180  ce eb d0 01 00 e6 95 c1  f6 18 5b 97 ed 61 d0 92  |..........[..a..|
00000190  94 51 f3 2c 5d 35 e5 2f  f1 8d 0c 1c f6 44 f8 05  |.Q.,]5./.....D..|
000001a0  d0 18 c1 05 ea b5 32 2c  50 21 a1 16 b0 24 c3 3a  |......2,P!...$.:|
000001b0  b1 53 29 a6 c7 c6 e2 e6  07 c2 00 78 16 8d 00 fe  |.S)........x....|
000001c0  ff ff 07 fe ff ff 00 08  00 00 14 82 14 16 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 d0 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  df 9f 78 00 18 1e 00 00  00 00 00 00 02 00 00 00  |..x.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c0 ef 76 8a 4e  4f 20 4e 41 4d 45 20 20  |..)..v.NO NAME  |
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
00000100  7d 00 66 b8 08 40 00 00  66 ba 00 00 00 00 bb 00  |}.f..@..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
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

Strange thing is that Gparted and the installer can not see the existing partition (partition table unrecognised in Gparted). It tells me that my whole hard drive is unallocated. However the script, which I think uses fdisk, can see the existing partitions.

Thanks for any help given.

---

### Post by sikander3786 on 2010-12-23
The problem seems to lie here.

> /dev/sda2 overlaps with /dev/sda3

And the solution, here.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by efflandt on 2010-12-23
Linux does not like to touch broken partitions.  I have seen many threads about overlapping partitions lately, but not "how" they ended up that way.  What tool did you use to do that, so others can avoid getting into that situation?

---

### Post by baster8 on 2010-12-23
To efflandt
I used partition wizard. I think it does some thing very hacky. Instead of aligning the extended partition correctly, it align the logical partition inside the extended partition immediately after the preceding partition. So now, there is some overhead/record-keeping-sector presumably from the extended partition that is overlapping with the preceding partition, and this overhead is not used somehow (?), which is why it works normally in windows. However, for Gparted, it thinks that this is corrupted partition table. I don't know how many partition software out there that does something like this or whether windows' own partition creator does the same thing, or whether Gparted maybe should learn to recognise this kind of thing (you can ignore this last statement, since I most likely don't know what I am talking about).

To sikander
Thank you very much. After fixing the partition, everything worked out fine. If  anyone else is interested in my solution, I just used the same partition software to shrink the preceding partition by a few hundred MB and leave it unallocated. Then after installing Ubuntu, one can optionally re-extend the partition back to original.

---

