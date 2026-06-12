---
title: "Windows XP not booting from Grub Menu"
date: 2012-03-24
forum: General Help
---

### Post by oslub on 2012-03-24
Hello everyone. This is my first post at ubuntu forum.

I am still a newbie at linux, having started with ubuntu 11.04 last year on my laptop.

On my old desktop, I decided to have a linux distribution as well, and use it together with windows XP SP3.

I tried ubuntu 11.10 first because it was the only distro I was familiar with and it is really easy to install and use from a windows user perspective, using WUBI.

However, it proved too heavy and slow for my old 1GB RAM, so after some googling, I decided to uninstall ubuntu (which was easy as well, not boot problems at all) and install Lubuntu.

So far so good, I am enjoying this distro very much, lightweight and very functional on my old desktop, all applications for my daily needs are running fine, customizable, it is exactly what I was looking for me and I will keep it.

However, after installing Lubuntu from a live usb, windows xp does not boot anymore when selected on Grub menu. When I choose Windows XP, the computer starts beeping loud as if it is in critical state and I have to reboot to go to grub menu again. I have seen my C: partition and all Windows files are there, so it is really a boot problem. I've already used UBCD4Win tool to fix mbr on disk0 (HDD) but it didn't work.

I've searched about this around this forums and there seems to be a solution "fixmbr" using Windows Recovery Console, after inserting WinXP installation disk. Unfortunatelly, both my IDE disk drives are not functional (this is a bit off topic, but I've tried everything, really everything to repair those drives, nothing seems to work! Please Visit this thread [[http://www.tomshardware.co.uk/forum/329145-10-disk-drives-reading]](http://www.tomshardware.co.uk/forum/329145-10-disk-drives-reading]), where I have all the solutions I've tried listed and if you know anything about disk drives that appear on windows explorer, bios settings, boot device menu, but always say that no media is present, please let me know of any solution. This is a problem which happens on lubuntu as well).

So any help about my WinXP booting problem would be very much appreciated. Please make it step by step solutions since I am still new at this. Thank you in advance. :p

---

### Post by idoitprone on 2012-03-24
download this script and run it and post the RESULT.txt in code tags

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by oslub on 2012-03-24
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 268532610 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63. According to the info in the boot 
                       sector, sda7 has 35660072 sectors, but according to 
                       the info from fdisk, it has 35664236 sectors.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    54,444,284    54,444,222   7 NTFS / exFAT / HPFS
/dev/sda2          54,444,346   315,420,209   260,975,864   f W95 Extended (LBA)
/dev/sda5          54,444,348   264,606,614   210,162,267   7 NTFS / exFAT / HPFS
/dev/sda6         264,606,678   268,526,474     3,919,797  82 Linux swap / Solaris
/dev/sda7         279,755,973   315,420,209    35,664,237   7 NTFS / exFAT / HPFS
/dev/sda8         268,527,616   277,676,031     9,148,416  83 Linux
/dev/sda9         277,678,080   279,754,751     2,076,672  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ECFC40F8FC40BE98                       ntfs       Disco Local
/dev/sda5        01CD0540EA3378A0                       ntfs       Disco local
/dev/sda6        3388f404-b5f6-4894-9e69-b40b90030ead   swap       
/dev/sda7        01CD0540ED0AB480                       ntfs       Recuperação
/dev/sda8        32a998c2-da5e-4c7b-8aa1-47c1a8744a27   ext4       
/dev/sda9        ec8423b2-49d6-4490-8d61-aa7bb5c225b8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 32a998c2-da5e-4c7b-8aa1-47c1a8744a27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 32a998c2-da5e-4c7b-8aa1-47c1a8744a27
  set locale_dir=($root)/boot/grub/locale
  set lang=pt_PT
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, com Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 32a998c2-da5e-4c7b-8aa1-47c1a8744a27
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=32a998c2-da5e-4c7b-8aa1-47c1a8744a27 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, com Linux 3.0.0-16-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 32a998c2-da5e-4c7b-8aa1-47c1a8744a27
    echo    'A carregar Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=32a998c2-da5e-4c7b-8aa1-47c1a8744a27 ro recovery nomodeset 
    echo    'A carregar ramdisk inicial ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, com Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 32a998c2-da5e-4c7b-8aa1-47c1a8744a27
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=32a998c2-da5e-4c7b-8aa1-47c1a8744a27 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, com Linux 3.0.0-12-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 32a998c2-da5e-4c7b-8aa1-47c1a8744a27
    echo    'A carregar Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=32a998c2-da5e-4c7b-8aa1-47c1a8744a27 ro recovery nomodeset 
    echo    'A carregar ramdisk inicial ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 32a998c2-da5e-4c7b-8aa1-47c1a8744a27
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 32a998c2-da5e-4c7b-8aa1-47c1a8744a27
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ECFC40F8FC40BE98
    drivemap -s (hd0) ${root}
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=32a998c2-da5e-4c7b-8aa1-47c1a8744a27 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda9 during installation
UUID=ec8423b2-49d6-4490-8d61-aa7bb5c225b8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-16-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ab b1 c1 fa c0 b7 d8 17  f6 03 a9 00 03 9c 74 75  |..............tu|
00000010  c0 39 7d 0c 98 33 c0 c4  80 29 03 27 25 30 7a 91  |.9}..3...).'%0z.|
00000020  a0 c1 20 a8 d2 06 b0 e4  ce 65 29 1f 17 0b 88 34  |.. ......e)....4|
00000030  40 64 82 49 7b 48 e4 e1  58 24 0a 03 12 00 3c c8  |@d.I{H..X$....<.|
00000040  6a 80 05 fa c9 00 00 18  d4 c1 42 e6 74 fd 09 00  |j.........B.t...|
00000050  00 00 00 04 80 06 a4 f9  15 a4 ec 37 d0 10 61 61  |...........7..aa|
00000060  a3 5f f7 ed 00 ef ff 07  38 dc a4 c8 16 c8 a1 e0  |._......8.......|
00000070  c9 82 d1 07 00 30 60 c6  00 2e 03 42 1d 60 7f fe  |.....0`....B.`..|
00000080  40 ae 06 c7 eb 03 e0 64  61 d9 0f ac 02 0c 74 d2  |@......da.....t.|
00000090  d5 01 e9 f5 31 70 ce 80  13 03 a8 0c a0 94 c0 e8  |....1p..........|
000000a0  43 82 0a 03 b1 3e 1f d0  92 3b 9b b1 84 64 40 2c  |C....>...;...d@,|
000000b0  10 c2 f0 90 09 1e e9 23  11 08 a3 81 30 0c 48 00  |.......#....0.H.|
000000c0  f0 40 94 22 00 12 a8 9e  00 00 18 d4 c1 42 e8 94  |.@.".........B..|
000000d0  ff 09 00 00 00 00 04 80  0e 2a 10 c6 91 24 0b 5f  |.........*...$._|
000000e0  41 4a bf 03 be fd 1f e0  48 93 2a 5b 20 de 1d 78  |AJ......H.*[ ..x|
000000f0  81 19 0b 9f 2c 98 78 00  00 03 68 0c f0 32 60 d4  |....,.x...h..2`.|
00000100  01 f7 e9 0f f0 6e 74 c0  3e 20 5e 46 c6 fd c0 2a  |.....nt.> ^F...*|
00000110  c0 00 27 5d 1d b0 6e 1f  03 ea 0c 40 31 c0 ca 00  |..']..n....@1...|
00000120  4a 09 8c 3a 24 e8 30 18  e9 f3 c1 ae 39 34 da 4b  |J..:$.0.....94.K|
00000130  c9 86 c4 02 22 0c 0e 99  e0 51 3e 22 79 38 1a 08  |...."....Q>"y8..|
00000140  c3 80 04 00 0f f2 4b 20  81 ee 09 00 00 18 d4 c1  |......K ........|
00000150  42 08 97 ff 09 00 00 00  00 04 80 0e 2a 10 07 92  |B...........*...|
00000160  28 4b 1d 41 ea 9e a0 61  63 6c aa ac 03 b4 fd 17  |(K.A...acl......|
00000170  48 67 27 5e 00 c6 82 27  0b 26 2c 00 c0 40 1a 03  |Hg'^...'.&,..@..|
00000180  bc 0c 1c 75 00 fe fa 03  bc 1d 1e af 0f 84 9f 91  |...u............|
00000190  75 3f b0 0a 30 e0 49 57  07 b0 df c7 c0 3a 03 50  |u?..0.IW.....:.P|
000001a0  0c b0 32 90 d2 07 ef fc  fb d9 62 51 3f 2f 12 34  |..2.......bQ?/.4|
000001b0  28 0e d4 19 81 d7 9c f9  4c e6 a4 83 82 61 00 fe  |(.......L....a..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 5b d2 86 0c 00 fe  |..........[.....|
000001d0  ff ff 05 fe ff ff 5d d2  86 0c f4 cf 3b 00 00 00  |......].....;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```Here it is the copy of the Results.txt

Thank you for your reply idoitprone.

---

### Post by bcbc on 2012-03-24
Please refer to this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You've overwritten the windows boot sector with grub.

---

### Post by oslub on 2012-03-24
> **bcbc said:**
> Please refer to this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You've overwritten the windows boot sector with grub.

Thank you so much!! This worked just fine. I can now boot windows xp and Lubuntu without any problem.
Thank you both for your much appreciated help.

---

