---
title: "Some how messed up windows MBR"
date: 2011-02-24
forum: General Help
---

### Post by LostMagix on 2011-02-24
So I was going by this howto:

[http://whyjoseph.blogspot.com/2009/07/bootable-backtrack-3-usb-drive-that.html](http://whyjoseph.blogspot.com/2009/07/bootable-backtrack-3-usb-drive-that.html)

working with windows 7 & backtrack

I havnt done anything in windows for years, im a bit rusty to tell you the truth.

I was working off a live boot, somehow the MBR on the windows partition was effected, now when try to do a normal boot I get "non-bootable disk"


I tried a recovery CD but I couldn't get anything to recognize the windows partition, I can still access it in linux however.

the HDD in question:

```
# fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4600c452

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    6  FAT16
/dev/sda2   *           6        2300    18432000    7  HPFS/NTFS
/dev/sda3            2300       60802   469913397+   7  HPFS/NTFS
```

I need to get this fixed ASAP, any help would be appreciated

---

### Post by LostMagix on 2011-02-24
also, grub is not install, im working with windows boot loader

---

### Post by wilee-nilee on 2011-02-24
> **LostMagix said:**
> also, grub is not install, im working with windows boot loader

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by LostMagix on 2011-02-24
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Im on a backtrack live-boot, its not to different from ubuntu

here's the ouput

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda2 starts at sector 80325.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

sdc1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4600c452

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         80,325    36,944,324    36,864,000   7 HPFS/NTFS
/dev/sda3          36,944,325   976,771,119   939,826,795   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2090 MB, 2090860544 bytes
2 heads, 63 sectors/track, 32410 cylinders, total 4083712 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x008eb5c0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     4,083,711     4,083,680   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0bcd68e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1           6,811,560     7,855,784     1,044,225  82 Linux swap / Solaris
/dev/sdc2    *             63     6,811,559     6,811,497   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        4D65-46FF                              vfat                                     
/dev/sda3        92E6732AE6730E2B                       ntfs       OS                            
/dev/sdb1        C0FF-DA89                              vfat                                     
/dev/sdc1        52e779a0-2779-49d3-9340-e1bc24397129   swap                                     
/dev/sdc2        4D65-63E4                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sdb1        /media/cdrom0            vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /mnt/sda2                vfat       (rw)
/dev/sda3        /mnt/sda3                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /mnt/sda1                vfat       (rw)


=========================== sdb1/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 0

# Boot automatically after 30 secs.
timeout 30

splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030

title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd800.gz
    .1GB: boot/initrdfr.gz
    .0GB: boot/initrd.gz
    .1GB: boot/vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  0e ac fe d6 04 c7 7e 88  ec 5a c5 1d 91 08 d7 f2  |......~..Z......|
00000010  7d 29 99 b3 21 be ad 67  5b 72 73 78 74 5a 87 9b  |})..!..g[rsxtZ..|
00000020  8f 9c 30 1b 3a 9b 38 9f  70 dd 13 1f 13 f1 7d 78  |..0.:.8.p.....}x|
00000030  95 08 17 b0 8e e3 95 01  60 dc f1 c8 59 4c e4 35  |........`...YL.5|
00000040  60 0a 63 64 02 db e5 a8  ec 90 f5 32 b5 3c b5 62  |`.cd.......2.<.b|
00000050  70 e0 0f 20 d9 ca 6b 58  e0 ef aa 36 9b e3 41 8f  |p.. ..kX...6..A.|
00000060  b5 7e 71 a7 81 c3 e3 49  88 9c 04 55 67 57 7b 3a  |.~q....I...UgW{:|
00000070  65 02 84 a7 47 47 c6 65  81 67 4a d4 d5 98 15 10  |e...GG.e.gJ.....|
00000080  36 34 b2 69 ec 38 88 eb  18 7b a8 41 7b b0 c6 39  |64.i.8...{.A{..9|
00000090  ef 89 6e 0d fe 9f fc 5d  fd db 81 da 34 90 4d 32  |..n....]....4.M2|
000000a0  46 56 cb 01 fd 7c e5 ba  5f 29 05 e8 17 f4 72 dd  |FV...|.._)....r.|
000000b0  15 54 aa da ad d2 28 62  3c 93 88 e2 86 39 d2 dc  |.T....(b<....9..|
000000c0  64 c6 80 d5 39 fb f4 a5  44 a8 88 c9 df 92 7b 0c  |d...9...D.....{.|
000000d0  a2 be 88 9c 14 5d 0e 35  1e 6e f4 76 e3 57 21 a6  |.....].5.n.v.W!.|
000000e0  45 5c ef 84 65 60 0d 32  de 30 d6 02 7b d5 bd aa  |E\..e`.2.0..{...|
000000f0  0f c8 cf fa 75 b9 0a c6  0d 63 58 fd ab 50 90 9d  |....u....cX..P..|
00000100  bb d7 1b 09 d2 47 b2 a4  3d 88 29 3b e4 30 57 44  |.....G..=.);.0WD|
00000110  c9 09 b9 51 79 00 77 ac  00 7d 9f a4 ea 0e a0 93  |...Qy.w..}......|
00000120  75 75 dd 81 22 99 2a f3  64 1d 37 54 ba 6a 86 07  |uu..".*.d.7T.j..|
00000130  1c 47 8e bd f6 e3 7e 30  96 7f ba 61 4d 1f 30 9a  |.G....~0...aM.0.|
00000140  fc 14 b9 6d 1f 94 ff b9  70 a6 cf 03 d7 4e 5e a9  |...m....p....N^.|
00000150  79 f9 3c 64 bf 74 fd b3  6b 6f 43 c9 ae e2 b2 a2  |y.<d.t..koC.....|
00000160  e1 40 4f fa 4a 73 d0 3e  fd 82 3d 17 b8 5f 0d 20  |.@O.Js.>..=.._. |
00000170  1c 58 c1 76 a2 41 56 ca  31 09 72 5e bf a8 3f 97  |.X.v.AV.1.r^..?.|
00000180  0b 77 53 01 3e 3d 52 66  81 2a 56 13 65 1d 8a 89  |.wS.>=Rf.*V.e...|
00000190  b4 63 1e 4a 3d c6 0e 56  82 ea 99 d8 38 69 19 04  |.c.J=..V....8i..|
000001a0  4b 1b 9e af bf 1d ec f6  55 3a 55 5c 80 bc 25 f9  |K.......U:U\..%.|
000001b0  1d f2 52 c0 d7 be b8 76  f1 11 88 59 13 b3 2f b6  |..R....v...Y../.|
000001c0  1b 44 34 8b f8 22 e2 09  60 3f 17 68 07 cc 20 87  |.D4.."..`?.h.. .|
000001d0  12 50 a5 aa 96 6a 0b 9c  e4 1a 26 08 52 20 7e 32  |.P...j....&.R ~2|
000001e0  c5 2f 41 b9 75 17 01 c8  74 dd 5a 0f 06 f6 a9 b3  |./A.u...t.Z.....|
000001f0  ea 29 8a e4 90 0c 93 55  18 ea ac b9 ce 1a 0e 9c  |.).....U........|
00000200


```

---

### Post by LostMagix on 2011-02-24
I tried installing lilo to /sda but it didnt help

at the very least I would think it would boot into lilo, its not reading anything at all.

---

### Post by wilee-nilee on 2011-02-24
Lets just see if a standard reload of the mbr works use this link to a visual understanding of getting to the command line in W7, and run this command when you get there; then reboot and see if your in.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
```
bootrec.exe /fixmbr
```

If your recovery disc isn't working here is one you can download.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by LostMagix on 2011-02-24
> **wilee-nilee said:**
> Lets just see if a standard reload of the mbr works use this link to a visual understanding of getting to the command line in W7, and run this command when you get there; then reboot and see if your in.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
```
bootrec.exe /fixmbr
```

If your recovery disc isn't working here is one you can download.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

/FixMbr didnt work

/ScanOs didnt see the windows install

---

### Post by wilee-nilee on 2011-02-24
Take a look at this link.
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

