---
title: "Grub installed on wrong disk"
date: 2011-11-05
forum: General Help
---

### Post by sublimestyle on 2011-11-05
My grub seems to be installed on the wrong disk, I cant boot Linux or the grub for that matter, says unknown file system when i try boot, from a live USB I ran the boot info script:

```
                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Grub2's core.img
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 32776 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

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
/dev/sda1              34         1,987         1,954 Data partition (Windows/Linux)
/dev/sda2           1,988 3,902,906,284 3,902,904,297 Data partition (Windows/Linux)
/dev/sda3   3,902,906,285 3,907,029,118     4,122,834 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63       112,454       112,392  de Dell Utility
/dev/sdb2             112,640    21,083,815    20,971,176   7 NTFS / exFAT / HPFS
/dev/sdb3    *     21,084,160   222,100,630   201,016,471   7 NTFS / exFAT / HPFS
/dev/sdb4         222,101,502   312,498,175    90,396,674   5 Extended
/dev/sdb5         222,101,504   306,280,447    84,178,944  83 Linux
/dev/sdb6         306,282,496   312,498,175     6,215,680  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 7743 MB, 7743995904 bytes
80 heads, 16 sectors/track, 11816 cylinders, total 15124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064    15,124,991    15,116,928   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        22D4AB62D4AB3747                       ntfs       
/dev/sdb1        07D9-0204                              vfat       DellUtility
/dev/sdb2        5EEE5FDAEE5FA8D3                       ntfs       RECOVERY
/dev/sdb3        BC4A63804A6335F4                       ntfs       OS
/dev/sdb5        8dc8baf1-756d-4058-b2f0-d5ad3b73b440   ext4       
/dev/sdc1        3ABF-2BAA                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=8dc8baf1-756d-4058-b2f0-d5ad3b73b440 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
#UUID=a47d7665-b376-4747-81db-3bda54b2ae6c none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

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

Unknown BootLoader on sdb4

00000000  8d 30 38 9d 8b d7 06 f8  93 80 8e 30 50 48 79 34  |.08........0PHy4|
00000010  27 25 11 ea 53 35 a6 99  9e 5d ae b2 c2 62 78 f7  |'%..S5...]...bx.|
00000020  0f a2 cf 11 5d a7 32 d9  4c ac d0 96 43 ca 86 6f  |....].2.L...C..o|
00000030  7c 27 a8 64 42 0f 85 e5  c3 32 85 89 c8 a6 ee 13  ||'.dB....2......|
00000040  95 9f 3c 7e c8 ba ea 2f  e6 1a f8 6b df c3 63 e6  |..<~.../...k..c.|
00000050  1a c8 9b 96 5d 76 d5 e6  66 69 d2 f6 36 62 a2 9a  |....]v..fi..6b..|
00000060  c6 dc b6 e2 61 af dd b1  c7 24 2e 12 03 86 68 89  |....a....$....h.|
00000070  e1 49 42 83 9f db f5 69  06 93 28 cd cb a3 9c b5  |.IB....i..(.....|
00000080  cc 8e 19 30 30 98 c2 a4  14 2b 30 90 1c 68 1c b9  |...00....+0..h..|
00000090  9d 15 ff fb b2 00 e3 8e  e4 20 68 d3 1b 2c 1b 70  |......... h..,.p|
000000a0  81 09 ba 73 65 86 5e 55  01 69 40 4e 3d 6d c2 69  |...se.^U.i@N=m.i|
000000b0  2c e8 49 c7 a1 bb 2a 74  19 8c 4f 0f 50 a4 38 d0  |,.I...*t..O.P.8.|
000000c0  5a 60 5e 55 ac a9 15 a4  35 1c 7e 84 89 1e 1b a7  |Z`^U....5.~.....|
000000d0  e2 62 c1 ab 1b e0 9f 26  28 e5 79 88 68 98 49 13  |.b.....&(.y.h.I.|
000000e0  1a 0b 83 13 cf 2f ac 07  d4 83 8c 45 8f a7 d4 67  |...../.....E...g|
000000f0  11 5e e4 50 3b 0b 68 ef  34 94 50 98 3c 13 0f 11  |.^.P;.h.4.P.<...|
00000100  c1 98 35 89 2d ae 9e 47  4f c5 7c 43 7c 7f fc bf  |..5.-..GO.|C|...|
00000110  4f 2d 0b ac 4b 4a 24 b4  a5 fd d1 f2 ab 34 d2 e8  |O-..KJ$......4..|
00000120  bc 70 8a 8b 73 57 bc 2b  db 69 66 57 16 50 c7 bd  |.p..sW.+.ifW.P..|
00000130  dd 3d 35 bc c1 30 ea 00  00 0b 72 9c e1 de 0c 55  |.=5..0....r....U|
00000140  58 dd c2 4c 88 2c c4 82  88 80 d1 35 c8 42 4c ca  |X..L.,.....5.BL.|
00000150  f6 22 d4 68 94 e2 ad 90  c7 43 15 4a b6 56 46 58  |.".h.....C.J.VFX|
00000160  67 a9 c4 1c 24 20 4d 80  ec 8f 3b 0b 60 c8 11 61  |g...$ M...;.`..a|
00000170  90 45 95 0e ce 76 b5 d3  11 3c 4e 34 0f a1 f4 a5  |.E...v...<N4....|
00000180  62 79 e2 d7 b0 ed 2c 7a  5b 73 da 2a a4 92 4d 52  |by....,z[s.*..MR|
00000190  a1 5a 74 53 29 46 bd ac  40 77 aa e6 bf a7 ec 7c  |.ZtS)F..@w.....||
000001a0  9f 65 3d 3b be 36 f7 75  51 ba 21 9d 57 0a 4c cc  |.e=;.6.uQ.!.W.L.|
000001b0  c1 e0 25 6b 05 70 e7 a3  5b 4e 3c 89 27 3b 00 fe  |..%k.p..[N<.';..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 78 04 05 00 fe  |...........x....|
000001d0  ff ff 05 fe ff ff 02 78  04 05 00 e0 5e 00 00 00  |.......x....^...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by raja.genupula on 2011-11-05
look at my signature for grub recovery i am sure that gonna help you . all the best man.

---

### Post by Rubi1200 on 2011-11-05
You have a number of different drives, GPT, and filesystem errors.

I recommend using a LiveCD to make backups before anything else and then investigate the problem using the advice below.

There is some great advice in this thread by oldfred:
[http://ubuntuforums.org/showthread.php?t=1868235&highlight=gpt](http://ubuntuforums.org/showthread.php?t=1868235&highlight=gpt)

---

### Post by oldfred on 2011-11-05
In addition, did you install Ubuntu and tell it to use a Windows /boot partition that was on sda?

Ubuntu repartitions 1+ to 2TB drives to gpt when you install to the large drive. I am not sure how you got the gpt on the 2TB drive otherwise. But you installed Ubuntu to sdb, but the boot loader is on sda. Always best to partition in advance and use manual install so you get the option to choose which drive to install grub to. But I like separating Operating Systems when you have two drives. Keeps windows (and its boot loader) on one drive and Ubuntu (and grub) on the other drive.

It looks like your Windows is missing its 100MB boot/recovery partition. You can repair your main install with a Windows 7 repair CD. Did you make that before doing anything else? Or do you have another Win7 or know someone with a Window 7 system?

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

