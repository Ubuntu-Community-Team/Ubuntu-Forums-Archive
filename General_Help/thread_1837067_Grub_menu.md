---
title: "Grub menu?"
date: 2011-09-01
forum: General Help
---

### Post by buttersauce on 2011-09-01
This randomly started today.  When i tried to boot into ubuntu it went to this GRUB menu but i can't figure out how to get it to just boot into ubuntu.  I am not by any means good at computers or anything.

Help?

---

### Post by coffeecat on 2011-09-01
I doubt whether it started randomly. You probably had a kernel upgrade and now the grub menu is offering you a choice of the new and previous kernels, as well as memtest. This is normal. How many menu choices do you have and what are they? You simply select which menu entry you want and press enter.

If you simply wait, grub will boot the first menu entry after a timeout of about 5 seconds.

---

### Post by buttersauce on 2011-09-01
> **coffeecat said:**
> I doubt whether it started randomly. You probably had a kernel upgrade and now the grub menu is offering you a choice of the new and previous kernels, as well as memtest. This is normal. How many menu choices do you have and what are they? You simply select which menu entry you want and press enter.

If you simply wait, grub will boot the first menu entry after a timeout of about 5 seconds.

There are a ton of menu choices it gives me.  I cannot even list them all, but i tried boot, and it said "no kernel selected" and i did not know what the kernel was called.  I am going to try just waiting and seeing if that will work.

---

### Post by coffeecat on 2011-09-01
> **buttersauce said:**
>  but i tried boot, and it said "no kernel selected"

That sounds as though something has gone wrong. Boot up with a live CD or live USB and choose "try Ubuntu". When you get to the desktop - you need an internet connection - go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for readability. That should tell us all we need to know.

---

### Post by buttersauce on 2011-09-04
> **coffeecat said:**
> That sounds as though something has gone wrong. Boot up with a live CD or live USB and choose "try Ubuntu". When you get to the desktop - you need an internet connection - go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for readability. That should tell us all we need to know.

Sorry it took me a while.  here are the results... i can make no sense of it...




=> Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 43704 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920     1,617,919     1,536,000   7 NTFS / exFAT / HPFS
/dev/sda3           1,617,920   381,559,814   379,941,895   7 NTFS / exFAT / HPFS
/dev/sda4         381,559,815   625,139,711   243,579,897   f W95 Extended (LBA)
/dev/sda5         381,559,878   620,928,314   239,368,437   7 NTFS / exFAT / HPFS
/dev/sda6         620,943,360   625,139,711     4,196,352   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        C28869BA8869AD9B                       ntfs       RECOVERY
/dev/sda3        4E426D99426D8715                       ntfs       OS
/dev/sda5        01CC5F4F3CC80BA0                       ntfs       PENDRIVE
/dev/sda6        4C85-BFF7                              vfat       READER
/dev/sdb1        3A22-02BB                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /cdrom                   fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


========================= sda5/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda5: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          0
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda5: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  5b 9f 55 f3 6f b0 3f b5  3b 78 b7 89 d3 a4 fe 2c  |[.U.o.?.;x.....,|
00000010  d4 1d b6 02 f7 37 0c de  93 e6 af a0 44 ee f7 f1  |.....7......D...|
00000020  5f 08 ee f1 95 1f 4d e0  80 7a ae d8 2d f0 7e 77  |_.....M..z..-.~w|
00000030  b9 10 1c 8c ce 56 eb ce  3f 63 56 86 99 19 ec 4a  |.....V..?cV....J|
00000040  ac e0 6b a0 27 cc c9 ac  17 c9 51 f2 84 d2 af f6  |..k.'.....Q.....|
00000050  fc 25 fa f3 28 68 c6 88  4d d7 40 69 f8 8d 27 0a  |.%..(h..M.@i..'.|
00000060  6b 8e ee 5e 4f 18 cc 72  27 bf c5 33 f3 af b4 0c  |k..^O..r'..3....|
00000070  bf c1 6d 9e 21 c5 c0 73  e6 aa 88 a2 80 a5 c2 8d  |..m.!..s........|
00000080  b9 6c 9d 8c 29 64 7f 97  cc c4 29 fd 9e e1 af 17  |.l..)d....).....|
00000090  1d 3f 99 eb df d5 f4 ec  21 39 4d 96 52 c8 e0 39  |.?......!9M.R..9|
000000a0  b1 e3 8f 8c d1 0c fd 79  25 36 9d b2 a3 ca bb 78  |.......y%6.....x|
000000b0  3c ff a1 3a 80 f6 83 4d  20 e3 b6 a2 8d 54 a7 68  |<..:...M ....T.h|
000000c0  7b 46 ed bd 6d 76 68 76  58 6e 41 b2 21 cc fc 8d  |{F..mvhvXnA.!...|
000000d0  34 65 9d ea 1e 81 8d 00  08 05 dd 29 55 a1 2d 7b  |4e.........)U.-{|
000000e0  2f 01 d0 83 1a 00 dc f6  7b d6 34 56 35 42 91 b9  |/.......{.4V5B..|
000000f0  2e ce b0 59 e1 df 34 5e  f3 05 e4 89 c7 1b 96 d2  |...Y..4^........|
00000100  f3 71 5d 38 f8 0a 7b 4f  ba c6 95 09 08 94 9c 57  |.q]8..{O.......W|
00000110  45 96 fa eb e6 6c 98 cd  09 42 eb 22 fe 17 04 d1  |E....l...B."....|
00000120  e5 f1 af 3e 2b f0 68 e3  2b a1 89 21 b0 18 38 cf  |...>+.h.+..!..8.|
00000130  9a 26 9e fb 4d 88 d5 a4  60 16 0f 53 22 fd 97 d8  |.&..M...`..S"...|
00000140  23 e3 eb f6 cc 17 c2 1a  f1 c9 29 02 54 36 8a 7a  |#.........).T6.z|
00000150  49 d8 b7 f2 31 92 12 4e  1e e9 76 7e 50 2c 6f 3f  |I...1..N..v~P,o?|
00000160  ce ad 2d be 00 de a6 49  2c 9f 99 11 14 4a ac b8  |..-....I,....J..|
00000170  7b 0a 6c 26 be e9 67 1e  64 13 3a 04 a4 00 a9 6c  |{.l&..g.d.:....l|
00000180  0b a7 99 f8 ea a4 38 d8  ff 7a fc a4 0a b9 c4 ec  |......8..z......|
00000190  44 25 d4 fb 07 f5 f9 81  4a fa 82 42 45 de 67 c2  |D%......J..BE.g.|
000001a0  f2 32 49 ff a0 ca 91 24  8b c5 6e 22 5e da f0 78  |.2I....$..n"^..x|
000001b0  d0 81 1a d5 34 0c e4 d1  fc ff 66 97 52 21 00 fe  |....4.....f.R!..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 f5 78 44 0e 00 fe  |......?....xD...|
000001d0  ff ff 05 fe ff ff ba b3  44 0e 3f 08 40 00 00 00  |........D.?.@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by coffeecat on 2011-09-04
Your boot script output shows that you have a wubi installation, but something is missing:

> **buttersauce said:**
> 
sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr


Under Boot files it should also show /ubuntu/disks/root.disk and /ubuntu/disks/swap.disk. These are files within the Windows filesystem but which act as the Ubuntu pseudo-partitions. They are not showing in the boot script output which suggests that they may have been deleted. Also missing from your boot script output are the contents of a number of system files from within your Ubuntu system. If the root.disk file is missing this would not be surprising.

Boot into Windows and open Computer. Now look in the C: drive. You will see a folder called "ubuntu". Open that. Is there a folder called "disks"? If there is, open that. What do you see inside the disks folder, if anything?

---

### Post by buttersauce on 2011-09-04
> **coffeecat said:**
> Your boot script output shows that you have a wubi installation, but something is missing:



Under Boot files it should also show /ubuntu/disks/root.disk and /ubuntu/disks/swap.disk. These are files within the Windows filesystem but which act as the Ubuntu pseudo-partitions. They are not showing in the boot script output which suggests that they may have been deleted. Also missing from your boot script output are the contents of a number of system files from within your Ubuntu system. If the root.disk file is missing this would not be surprising.

Boot into Windows and open Computer. Now look in the C: drive. You will see a folder called "ubuntu". Open that. Is there a folder called "disks"? If there is, open that. What do you see inside the disks folder, if anything?

There is no Disks folder in the ubuntu file. Just "install, winboot, Ubuntu, unintstall ubuntu"  

At this point i could i just delete the entire part of my hard drive thats Ubuntu and reinstall it?  I dont have antyhing of importance over there.

---

### Post by coffeecat on 2011-09-04
> **buttersauce said:**
> There is no Disks folder in the ubuntu file. Just "install, winboot, Ubuntu, unintstall ubuntu"  

At this point i could i just delete the entire part of my hard drive thats Ubuntu and reinstall it?  I dont have antyhing of importance over there.

No disks folder? Curious. Did you delete it yourself? 

Rather than delete anything else, I suggest you open the Windows Control Panel and use that to uninstall the Ubuntu wubi installation. Although most of it is missing already, the Windows registry needs editing by the uninstaller. If you simply delete things manually, you might run into problems re-installing if the registry thinks there is still a wubi installation there.

---

