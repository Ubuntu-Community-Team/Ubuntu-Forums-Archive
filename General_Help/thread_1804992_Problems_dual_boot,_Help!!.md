---
title: "Problems dual boot, Help!!"
date: 2011-07-15
forum: General Help
---

### Post by dmodolo on 2011-07-15
I have read already few threads related to my problem, but no one was sufficient to solve it.

I had windows 7 in my laptop and I decided to install Ubuntu 11.04. 

During the installation I split a big partition of 400gb (which only 100gb used by windows) in 2gb swap and 100gb ext4 for ubuntu. However, the 400gb partition that initially was labeled as 'type' 'ntfs', now doesn't have any type and under the field 'Used' there is written 'unknown'. 

There was no way to go back to the previous state and I completed the installation. Since that I haven't been able to boot Windows 7 anymore. In the GNU GRUB, besides the Ubuntu lines, I have 2 new options: 
*Winfows Recovery Environment (loader) (on /dev/sda1)*
*Windows 7 (loader) (on /dev/sda2) *

where the command for booting the second one is:
```
setparams 'Windows 7 (loader) (on /dev/sda2)'

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 9A .... 4B
chainloader + 1
```

and if I try to boot it the windows boot manager says: 'Windows failed to start. .... The boot selection failed because a required device is inaccessible'

Moreover, if I try to boot *Winfows Recovery Environment (loader) (on /dev/sda1)* it ends up in Acer eRecovery Management where I can only completely restore system to factory defaults (where all C: drive will be deleted). The other options are not available!!! 

The situation of my disk is the following:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0748d562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Unknown
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS
/dev/sda3        27469824   222782323    97656250   83  Linux
/dev/sda4       222783486   976771071   376993793    5  Extended
/dev/sda5       222783488   226689023     1952768   82  Linux swap / Solaris
/dev/sda6       226691072   976771071   375040000   83  Linux


```

Please help me!!! I really need to have windows back without loosing any file, and very soon (I need to finish my thesis). 

Thank you so much,
Davide

ps. Ubuntu is running properly and I will not have my windows cd for the next 3-4 weeks.

---

### Post by Ad@m on 2011-07-15
/dev/sda1            2048    27265023    13631488   27  Unknown -----> Gone wrong??

It seems your main Windows 7 ntfs  partition has gone wrong, unfortunately that can happen when resizing.

In future I recommend backing up important files before you proceed with such an operation. 

You can safely try a program called testdisk to make an assessment on the unknown partition although the outcome is not a definitive answer as to the recoverability of the partition. 

sudo apt-get install testdisk
sudo testdisk

Quick steps

1. no log
2. select your disk
3. Intel / PC Partition
4. Analyse
5. Do a 'Quick search' on the unknown partition

If a quick search fails you could try a deeper search.

What does test disk report on the unknown partition?

---

### Post by dmodolo on 2011-07-15
ok! I am running it now, but it seems a bit slow. I will write here the results as soon as it finishes.

Anyway... Do you think I will be able to recover my data? 

Thanks

---

### Post by smurphy_it on 2011-07-15
If all else fails, boot a live linux CD, hook up an external USB drive (if you have one) and copy the pertinent data to it.  Then do a windows 7 system recovery, and put it "back to factory defaults".

At least you'll have your data to put back in.

Just backup your C:\Users folder, and any others off of root which are important.  Check your C:\Program Files for any other applications and potential data first.

---

### Post by dmodolo on 2011-07-15
> **smurphy_it said:**
> If all else fails, boot a live linux CD, hook up an external USB drive (if you have one) and copy the pertinent data to it.

How can a live linux CD access the data that was in windows? And what should I actually do? I can run ubuntu, but I can't mount that partition!

Thanks

---

### Post by rickytikki on 2011-07-15
a live cd runs form the cd so there will be no hard drive mounted so u can mount and extracct to a usb

---

### Post by Ad@m on 2011-07-15
The OP's NTFS partition is being registered as unknown, Ubuntu cannot therefore mount it.

---

### Post by dmodolo on 2011-07-15
Waiting for the testDisk I run the boot Info Script and this is the result:

>              Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,265,024    27,469,823       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,469,824   222,782,323   195,312,500  83 Linux
/dev/sda4         222,783,486   976,771,071   753,987,586   5 Extended
/dev/sda5         222,783,488   226,689,023     3,905,536  82 Linux swap / Solaris
/dev/sda6         226,691,072   976,771,071   750,080,000  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63 1,953,520,064 1,953,520,002   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F6F27DB0F27D7629                       ntfs       PQSERVICE
/dev/sda2        9AC67EFAC67ED64B                       ntfs       SYSTEM RESERVED
/dev/sda3        c423f80f-507a-4304-ab8d-d54b0bab692a   ext4       
/dev/sda5        def0c5ea-05ad-47fb-b9b1-0cc4c01d76d2   swap       
/dev/sdb1        8A36-16E0                              vfat       DAVIDE_PHD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/DAVIDE_PHD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root c423f80f-507a-4304-ab8d-d54b0bab692a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root c423f80f-507a-4304-ab8d-d54b0bab692a
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c423f80f-507a-4304-ab8d-d54b0bab692a
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=c423f80f-507a-4304-ab8d-d54b0bab692a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c423f80f-507a-4304-ab8d-d54b0bab692a
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=c423f80f-507a-4304-ab8d-d54b0bab692a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c423f80f-507a-4304-ab8d-d54b0bab692a
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c423f80f-507a-4304-ab8d-d54b0bab692a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c423f80f-507a-4304-ab8d-d54b0bab692a
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c423f80f-507a-4304-ab8d-d54b0bab692a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c423f80f-507a-4304-ab8d-d54b0bab692a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c423f80f-507a-4304-ab8d-d54b0bab692a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root F6F27DB0F27D7629
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 9AC67EFAC67ED64B
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=def0c5ea-05ad-47fb-b9b1-0cc4c01d76d2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  75.233169556 = 80.781000704   boot/grub/core.img                             1
  23.395668030 = 25.120907264   boot/grub/grub.cfg                             1
  14.651912689 = 15.732371456   boot/initrd.img-2.6.38-10-generic              2
  13.563995361 = 14.564229120   boot/initrd.img-2.6.38-8-generic               2
  13.985664368 = 15.016992768   boot/vmlinuz-2.6.38-10-generic                 1
  75.231449127 = 80.779153408   boot/vmlinuz-2.6.38-8-generic                  1
  14.651912689 = 15.732371456   initrd.img                                     2
  13.563995361 = 14.564229120   initrd.img.old                                 2
  13.985664368 = 15.016992768   vmlinuz                                        1
  75.231449127 = 80.779153408   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  3e b9 2e ff cf 1e 5f b1  63 b5 6f d5 30 a1 9f 32  |>....._.c.o.0..2|
00000010  84 2c 00 5b 95 39 2c 97  4f 16 52 0d 59 75 ba 58  |.,.[.9,.O.R.Yu.X|
00000020  1f 7a 43 dc 3b 5f b4 52  58 17 03 71 4c a1 4e 14  |.zC.;_.RX..qL.N.|
00000030  c4 00 1e a1 dc 5c 95 10  84 af 53 fd 14 7f 3d bc  |.....\....S...=.|
00000040  c2 aa cc e8 b1 a3 e0 be  56 23 0f fc 7f 03 28 51  |........V#....(Q|
00000050  ab 31 d9 f1 3d 6e cc b0  28 e8 69 ce 5b eb a4 6c  |.1..=n..(.i.[..l|
00000060  4d 61 af 74 ce a8 37 52  f8 ae ef 34 11 90 60 4a  |Ma.t..7R...4..`J|
00000070  40 20 3c 67 dd 9e 96 2e  e0 1e 11 51 87 52 ce 19  |@ <g.......Q.R..|
00000080  a6 06 25 48 51 8f 42 0b  48 17 65 47 31 98 5e c6  |..%HQ.B.H.eG1.^.|
00000090  b6 d8 f4 41 f2 94 49 55  39 d0 66 8e b2 c9 62 12  |...A..IU9.f...b.|
000000a0  fa db 2e 86 7c 93 0c 16  6a 3e ee 27 24 99 94 af  |....|...j>.'$...|
000000b0  aa 36 0a 05 df 25 3c c2  d9 24 8f 54 6e 72 9f 5c  |.6...%<..$.Tnr.\|
000000c0  12 25 db 81 73 2a 54 72  6f 3c 51 37 c6 55 97 61  |.%..s*Tro<Q7.U.a|
000000d0  a3 fd c6 49 d0 9e 09 87  96 5e 87 9d 84 4c aa 36  |...I.....^...L.6|
000000e0  a0 5e 48 77 68 8e 6a 4f  87 9e 5e 01 de 93 45 69  |.^Hwh.jO..^...Ei|
000000f0  ef c5 a8 fd 7b b7 ab 0e  92 5f a4 5a 69 62 39 68  |....{...._.Zib9h|
00000100  66 cd 1e ea ac 58 d7 92  48 ed 50 04 22 b6 76 80  |f....X..H.P.".v.|
00000110  91 79 56 78 28 4f a6 2b  88 4a 29 50 ad 3a d2 48  |.yVx(O.+.J)P.:.H|
00000120  ad 59 2b ea 39 45 4c 28  27 05 75 19 38 ea 23 3e  |.Y+.9EL('.u.8.#>|
00000130  bd b3 39 40 23 37 7b 19  97 69 72 47 86 b0 8e cf  |..9@#7{..irG....|
00000140  a8 de b6 33 6d cd ed 67  36 b9 84 a0 9f 47 cc 20  |...3m..g6....G. |
00000150  13 ad 65 16 c8 8f d4 93  1c 6f de 50 5d 89 60 5f  |..e......o.P].`_|
00000160  5b fb 27 6a 01 92 49 da  d9 37 22 ed 5e 83 1a 7d  |[.'j..I..7".^..}|
00000170  3f 10 8b 2c b8 59 8a 22  09 cc 26 47 54 54 f1 be  |?..,.Y."..&GTT..|
00000180  7c 63 1a 23 88 f2 16 5a  c5 87 51 59 58 20 72 3c  ||c.#...Z..QYX r<|
00000190  cc 19 ab ae 69 8f cb 3f  57 e8 27 47 a2 ff 04 0b  |....i..?W.'G....|
000001a0  55 4f 8c a5 a4 19 31 80  3b 86 5b 25 dc 79 1f f3  |UO....1.;.[%.y..|
000001b0  9e ae 1c 92 f1 c1 7d d8  54 54 84 12 8d 6b 00 fe  |......}.TT...k..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 98  3b 00 00 58 b5 2c 00 00  |........;..X.,..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda6

00000000  44 dd 79 6a c4 57 dc ff  8b 8c c4 24 8a 69 26 fd  |D.yj.W.....$.i&.|
00000010  11 1d 92 d2 ff 32 46 16  d9 95 e8 f4 23 63 16 30  |.....2F.....#c.0|
00000020  63 07 e1 c9 a5 bd 5b 06  35 cf 42 31 f7 3b 02 14  |c.....[.5.B1.;..|
00000030  3b a6 ae 9e b9 27 95 6f  ef d4 12 5e 00 af f9 c6  |;....'.o...^....|
00000040  33 db eb 63 9c 41 e2 da  bf fd 77 f8 76 81 8f 3f  |3..c.A....w.v..?|
00000050  41 65 21 16 c1 57 d8 d7  cc 51 a1 63 c0 43 ec ba  |Ae!..W...Q.c.C..|
00000060  0d e4 6a 04 da bf fa 0f  77 80 ec ee 7f fd 25 c5  |..j.....w.....%.|
00000070  d3 0e 5d e4 70 c0 65 a0  cc 30 46 dc 06 e3 45 18  |..].p.e..0F...E.|
00000080  41 dc a7 fa bf f8 5a 85  3f 71 6b fe 69 61 df 2f  |A.....Z.?qk.ia./|
00000090  20 24 e9 f2 64 43 be d8  72 75 7d 7e a1 ee 86 62  | $..dC..ru}~...b|
000000a0  0b b1 5d c8 e8 36 0c 7b  db 37 b1 57 bf f4 36 7e  |..]..6.{.7.W..6~|
000000b0  1f ce 0d 53 82 d1 34 87  b5 1d 87 08 cd c6 76 54  |...S..4.......vT|
000000c0  35 6e 70 76 f8 c6 0d e4  7a b5 ff 61 eb 49 d2 78  |5npv....z..a.I.x|
000000d0  f5 ff 25 60 e4 9e 46 ee  5a 82 73 af cf ef d8 20  |..%`..F.Z.s.... |
000000e0  ba 37 15 85 19 5a bb d4  14 b6 42 38 e6 0f 3d 6b  |.7...Z....B8..=k|
000000f0  3f c3 d2 0e ef 81 e3 f1  ca 76 ca ce db 66 7d 1b  |?........v...f}.|
00000100  14 e3 56 10 0d b0 4f db  bd fc be b6 62 15 8d 97  |..V...O.....b...|
00000110  06 d2 7b c0 ed da 04 33  89 1c 82 ee 17 35 2d 08  |..{....3.....5-.|
00000120  27 df 99 54 97 08 14 1f  e3 3f 8c f7 be ce 62 0a  |'..T.....?....b.|
00000130  6f bf ca 40 a7 52 6c b5  41 09 56 10 3c 66 ca 33  |o..@.Rl.A.V.<f.3|
00000140  2d 8e ea 11 96 d4 82 b4  99 66 32 df b2 4d c8 a8  |-........f2..M..|
00000150  83 e3 61 f2 6d 6e 03 cd  c2 06 94 ce 43 81 ab b5  |..a.mn......C...|
00000160  f0 3e 76 94 34 7d c3 ee  c2 ea a0 c4 51 a5 e6 6f  |.>v.4}......Q..o|
00000170  7d 06 0e 2a 3e 4b 6f bb  fd 1c 60 ce 8b 72 2e 32  |}..*>Ko...`..r.2|
00000180  39 72 b6 66 e6 32 e5 a7  5b 33 bd 65 0c 79 1a 33  |9r.f.2..[3.e.y.3|
00000190  7f 33 0f f8 da c0 b1 80  c6 fc fe 05 31 70 86 0d  |.3..........1p..|
000001a0  e2 da ca 35 fb e8 e8 33  d0 41 f4 c9 e4 15 0c 7a  |...5...3.A.....z|
000001b0  d0 36 63 09 0f 90 5f ff  82 0d a3 e0 63 dc ec f7  |.6c..._.....c...|
000001c0  3c 6b d6 90 71 12 40 73  7e 6d ff c6 c8 6d 97 d8  |<k..q.@s~m...m..|
000001d0  17 ea a8 10 d5 ce 1e d5  e5 81 e2 c5 63 bd 19 bc  |............c...|
000001e0  a1 73 20 5b fd 36 67 65  c0 63 6c 5c c9 0f 97 15  |.s [.6ge.cl\....|
000001f0  44 ca f2 fc 56 ff 15 b7  75 79 7c 86 23 16 57 05  |D...V...uy|.#.W.|
00000200

Unknown BootLoader on sdb1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 40 20 00  |.X.BSD  4.4..@ .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  82 59 70 74 49 a3 03 00  00 00 00 00 02 00 00 00  |.YptI...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e0 16 36 8a 44  41 56 49 44 45 5f 50 48  |..)..6.DAVIDE_PH|
00000050  44 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |D FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error



---

### Post by Ad@m on 2011-07-15
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,265,024    27,469,823       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,469,824   222,782,323   195,312,500  83 Linux
/dev/sda4         222,783,486   976,771,071   753,987,586   5 Extended
/dev/sda5         222,783,488   226,689,023     3,905,536  82 Linux swap / Solaris
/dev/sda6         226,691,072   976,771,071   750,080,000  83 Linux
```If /dev/sda1 is your recovery partition, then I think you should stop the test disk analysis.

/dev/sda2 = the 100MB Windows 7 partition

The rest are your Linux partitions.

Are you sure you resized your windows partition? It looks more like it was deleted.

EDIT: Infact Looking at the partition file sizes using your fdisk output, with sda1 at about 13GB is certainly does look like a recovery partition. I apologize for sending you on a wild goose chase.

---

### Post by dmodolo on 2011-07-15
Yes I did, or at least I though!! 
What should I do now to recover the data and run Windows? 

Thank you so much for your time.

---

### Post by Ad@m on 2011-07-15
You are pretty much in a terrible situation, how valuable is it to get the data back?

When you delete a partition / format a disk, all the data that was present doesnt disappear, it just becomes in inaccessible unless it has been physically over written with data.

So if your Ubuntu installation has not overwritten the same disk location containing an important document then it is possible to recover that document using programs such as photorec which use data carving techniques to recover files.

However this is a long process and can only be achieved using a separate system. 

And the real bummer is if all your original content (the files you wish to recover) has been over written with new data then you wont be able to recover it.

I think you should start re-writing your thesis.

---

### Post by Blasphemist on 2011-07-15
Time out please. I don't think this is such a mess. sda2 is the windows partition and it looks good. sda3 is the ubuntu install and it looks good. sda6 is an unknown linux partition and it has an issue. The mbr isn't reporting errors in the boot script. Time out for a bit and let's look in more detail and make sure the next step is right. I want to stop you from doing something destructive so I'm going to post this now and look into this in more depth. I also know of a few users that are real good at this and I'll see if any of them appear to be on line and ask them to take a look.

---

### Post by Ad@m on 2011-07-15
Blasphemist, I am going according to the fdisk output. 

Do you believe it is wrong? Is the bootscript output more reliable?

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0748d562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Unknown
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS
/dev/sda3        27469824   222782323    97656250   83  Linux
/dev/sda4       222783486   976771071   376993793    5  Extended
/dev/sda5       222783488   226689023     1952768   82  Linux swap / Solaris
/dev/sda6       226691072   976771071   375040000   83  Linux
```

---

### Post by idoitprone on 2011-07-15
> **Ad@m said:**
> Blasphemist, I am going according to the fdisk output. 

Do you believe it is wrong? Is the bootscript output more reliable?



Well fdisk is only used to find partition number, type, and size. It does not show much; however, bootscript does that plus alot more. Made by forum geniuses.

OP, I wonder what is the integrity of your whole windows partition.

 I wonder if you can get a windows repair disk and use chkdsk. I cant find any problems with you boot script. What brand do you have? I might want to avoid it lol

If that passes the chkdsk. I say get is window 7 or vista recovery cd and repair the boot files. That might also be the issue.

If all of those have failed, windows has screwed us with a new version of ntfs

---

### Post by Blasphemist on 2011-07-15
First, I did ask one of the moderators that is very good to take a look at this thread. Hopefully he'll have a chance to do that. 

I do see what you are referring to adam in that sda2 is real little. So to me it doesn't seem deleted but rather really shrunken. Davide, could you tell us the complete sequence of events in as much detail as you can? Somehow 2 partitions for linux got created, sda 3 and sda6, and sda3 didn't get created in the extended partition as would be normal. 

David or Davide, I don't know if that was a typo earlier, there may be bad news ahead but lets not give up. As Adam said, this could be bad if sda3 has overwritten what was where windows was on the disk. There are some pretty good utils and people with skills here though. Try this for if you would. Boot to the live cd and run GParted. Please post screen shots of sda. Also, try to mount sda2 and sda3 from that program. Then run nautilus, the file manager, and see what if anything can be seen on those partitions. You can right click on a partition in GParted to mount it. I don't think we should go further than that just yet unless someone comes up with a good and safe plan.

---

### Post by idoitprone on 2011-07-15
> **Blasphemist said:**
> First, I did ask one of the moderators that is very good to take a look at this thread. Hopefully he'll have a chance to do that. 

I do see what you are referring to adam in that sda2 is real little. So to me it doesn't seem deleted but rather really shrunken. Davide, could you tell us the complete sequence of events in as much detail as you can? Somehow 2 partitions for linux got created, sda 3 and sda6, and sda3 didn't get created in the extended partition as would be normal. 

David or Davide, I don't know if that was a typo earlier, there may be bad news ahead but lets not give up. As Adam said, this could be bad if sda3 has overwritten what was where windows was on the disk. There are some pretty good utils and people with skills here though. Try this for if you would. Boot to the live cd and run GParted. Please post screen shots of sda. Also, try to mount sda2 and sda3 from that program. Then run nautilus, the file manager, and see what if anything can be seen on those partitions. You can right click on a partition in GParted to mount it. I don't think we should go further than that just yet unless someone comes up with a good and safe plan.


lol Your 666th bean you demon

---

### Post by Blasphemist on 2011-07-15
I know, I wish I could keep it at 666 somehow :D

I wonder is sda6 is just not formatted. If so, that may be good for recovery. Anyway, please tell me just what went on with running testdisk. What did it show and what did you do with it? How did you stop it and has it told you of any helpful status or issues?

Can sdb partitions be mounted and accessed from booting to the cd? If so good as that would provide a place to copy to if anything can be salvaged along the way.

---

### Post by Blasphemist on 2011-07-15
Since we haven't heard back on the answers to the questions yet, I have been looking at the testdisk wiki. I'm real interested to know if the deeper search might find your thesis. I'd be real careful with what you do in testdisk but I do think it may help a lot. I know I've seen someone involved in that project on these forums and maybe they'll see this.

---

### Post by Hugh971 on 2011-07-15
I'm rather tired so apologise in advance for the quality of this post.

I've sort of skim read this so I may be wrong in what I'm saying but to me it looks like the situation is as follows;

[LIST]
[*] Windows 7 (unlike XP) uses a seperate boot partition. I think in this case that's sda2. The boot partition doesn't contain any user data.
[*]sda1 was your windows operating system partition with all your data on.
[*]when resizing the disk (if you did resize the partition instead of delete it) something screwed up and destroyed the partition.
[*]the data is most likely still there on that partition and can potentially be recovered.
[*]the more you use your computer the more likely it is that your data can be overwritten (as the space is unallocated and can be used as far as the computer is interested)
[/LIST]
To fix this I would download Hiren's Boot CD and see if any of the data recovery software can get your data back. Failing this you could professionally pay for your data to get recovered.

If you have already restored windows using the acer utility though it maybe too late as its much more likely the data has been overwritten.

---

### Post by drs305 on 2011-07-15
I'm a very infrequent Windows user and know only the basics of how Windows boots. Normally W7 has a 100MB /boot partition and then a normally-sized main partition. I looks like sda2 was the original W7 boot partition since it is small and contains /bootmgr and /Boot/BCD, which are two critical boot components. What's missing is the /Windows/System32/winload.exe file, although that is only a minor problem.

The RESULTS.txt seems to indicate that the main Windows partition was overwritten at some point. 

Without the boot info script, I would normally have recommended running chkdsk and then trying the Windows recovery disks to restore the bootloader. However, those efforts would not have recovered the partition if what I think happened is the case.

Testdisk can look at the disk and sometimes with a deep search come up with recoverable partitions and folders, but it depends greatly on what's been written to the disk in the meantime. It has a companion app called Photorec but I've never used it and it doesn't recover files by filename. I'd probably try a Windows recovery app if you know of one or someone else can provide a recommendation.

Here is a TestDisk link if you haven't seen it yet:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

---

### Post by dmodolo on 2011-07-18
What happend was:

- windows 7 was installed and present in a big HD of 500gb that was not partitioned.
- I started installing Ubuntu. I choose to extract 2gb from the 500gb for swap, but during the partitioning something went wrong and the system crashed.
- I re-booted and the partition was now labeled as unknown.
- I continued the installation of Ubuntu partitioning this unknown partition in 2gb swap and 100gb for Ubuntu.

I don't remember whether when partitioning I chose swap and Ubuntu to go to the end of the unknown partition or not (but I think I did).

---

### Post by Blasphemist on 2011-07-18
Nothing has changed since a couple days ago right? 

From GParted, whether you are booted to Ubuntu installed on the hard disc or running from the installation media, you can right click on the windows partitions and see if mount is an option. If the partition is already mounted, unmount will be the option. Do you succeed in mounting any partitions not already mounted? 

Mounted partitions will show up in nautilus (the file manager) in ubuntu. Can you access any files that you need to recover in this manner? If so, I'd copy them to removable media.

If at this point you do not have the files recovered that you need, you need to try recovery options. I don't know if that will be successful or not as it seems likely windows has been overwritten. There are programs that can take a look at the hard drive and possibly recover files. The testdisk and its companion photorec program might work. There are others that might work.

It appears you made an error during the installation. Don't worry, you weren't the first nor will you be the last. It happens even though the installation screens are created to try and prevent that yet still give experienced users pretty complete control. 

Your partitions are not setup well right now. My recommendation is to recover anything important and possible to recover and then start over with a good plan. Would you like further help today with attempting recovery? If so, please answer my questions in this post and look back at the other posts and provide all the answers you can.

---

