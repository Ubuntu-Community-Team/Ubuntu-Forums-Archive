---
title: "Problem with dual boot and Grub 2 menu."
date: 2011-07-26
forum: General Help
---

### Post by Perplexed Pat on 2011-07-26
I have dual boot ubuntu 10.10 & XP but my Grub menu has started to load ubuntu without giving me a chance to load XP. It just flashes on for a second without giving me time. I followed the instructions from [here]("http://ubuntuforums.org/showthread.php?t=1581099") to purge and reinstall Grub 2.
[URL="http://ubuntuforums.org/showthread.php?t=1581099"]
[/URL]My etc/default/grub reads:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=30
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```and my boot info script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda5 starts at sector 156114944. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    48,925,682    48,925,620   7 NTFS / exFAT / HPFS
/dev/sda2          48,926,718   156,301,311   107,374,594   f W95 Extended (LBA)
/dev/sda5         156,114,944   156,301,311       186,368   6 FAT16
/dev/sda6          48,926,720   156,112,895   107,186,176  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 10.3 GB, 10262568960 bytes
240 heads, 63 sectors/track, 1325 cylinders, total 20044080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    20,033,999    20,033,937   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        40F07DB2F07DAEB2                       ntfs       
/dev/sda5        11DF-1F3B                              vfat       
/dev/sda6        2374313b-ec20-41f3-b7f7-4aabaa43ab59   ext4       
/dev/sdb1        F8AA-D1B0                              vfat       Slave

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 2374313b-ec20-41f3-b7f7-4aabaa43ab59
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 2374313b-ec20-41f3-b7f7-4aabaa43ab59
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 2374313b-ec20-41f3-b7f7-4aabaa43ab59
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=2374313b-ec20-41f3-b7f7-4aabaa43ab59 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 2374313b-ec20-41f3-b7f7-4aabaa43ab59
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=2374313b-ec20-41f3-b7f7-4aabaa43ab59 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 2374313b-ec20-41f3-b7f7-4aabaa43ab59
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2374313b-ec20-41f3-b7f7-4aabaa43ab59 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 2374313b-ec20-41f3-b7f7-4aabaa43ab59
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2374313b-ec20-41f3-b7f7-4aabaa43ab59 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" --users pat {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 2374313b-ec20-41f3-b7f7-4aabaa43ab59
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 2374313b-ec20-41f3-b7f7-4aabaa43ab59
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 40F07DB2F07DAEB2
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro,user_xattr 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  29.498088837 = 31.673331712   boot/grub/core.img                             1
  51.683448792 = 55.494680576   boot/grub/grub.cfg                             1
  24.634765625 = 26.451378176   boot/initrd.img-2.6.35-22-generic              2
  52.902637482 = 56.803774464   boot/initrd.img-2.6.35-30-generic              3
  29.584075928 = 31.765659648   boot/vmlinuz-2.6.35-22-generic                 1
  29.588081360 = 31.769960448   boot/vmlinuz-2.6.35-30-generic                 1
  52.902637482 = 56.803774464   initrd.img                                     3
  24.634765625 = 26.451378176   initrd.img.old                                 2
  29.588081360 = 31.769960448   vmlinuz                                        1
  29.584075928 = 31.765659648   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  5c a3 7d f9 e4 85 67 b2  b3 e7 14 e5 e3 62 d8 c6  |\.}...g......b..|
00000010  94 78 18 ff cd 52 21 ac  14 40 2e 7b 58 ce 0a 4d  |.x...R!..@.{X..M|
00000020  ab 90 a5 3e b6 5e 08 83  16 b7 3c ac b5 2f c7 d2  |...>.^....<../..|
00000030  b7 f1 7e ba b0 a9 39 09  4c 8b 06 c0 fa 89 a0 90  |..~...9.L.......|
00000040  79 6c 85 89 5f e7 a2 dc  b7 ed 27 f2 ce 2b 26 36  |yl.._.....'..+&6|
00000050  c5 ad 71 b5 46 a2 ac 90  d9 2a f4 1a 44 07 f8 10  |..q.F....*..D...|
00000060  73 90 d3 a6 3d d6 89 31  fe 72 2a 0e a3 20 aa d4  |s...=..1.r*.. ..|
00000070  b9 88 2a a8 98 47 a6 c6  76 51 d0 b9 c2 d0 0a 46  |..*..G..vQ.....F|
00000080  33 23 e2 e3 cb 1e db 08  f7 41 09 ac fa f1 f5 3b  |3#.......A.....;|
00000090  ea 4b b0 d0 5f 35 57 ce  59 17 3b 5c b7 a1 11 03  |.K.._5W.Y.;\....|
000000a0  05 d4 2e 48 f3 36 fd b2  fe ea 99 c1 17 81 94 1a  |...H.6..........|
000000b0  13 bd 67 ce 27 bb 50 7f  54 6f 17 af c5 0e 51 27  |..g.'.P.To....Q'|
000000c0  12 7a f0 63 41 56 c0 fe  78 b0 1a f5 f3 c5 52 9c  |.z.cAV..x.....R.|
000000d0  72 1a a8 23 e7 22 6d 4f  5a 7e 00 5e 6b d5 08 bc  |r..#."mOZ~.^k...|
000000e0  d4 b1 dd b8 91 8b b8 51  0c cd 04 4f ce 44 32 6f  |.......Q...O.D2o|
000000f0  4d 8b 06 15 da ed b3 6c  72 31 9e 0f 99 0c 80 4b  |M......lr1.....K|
00000100  6f 85 c1 81 17 42 c2 2c  c0 23 6d 82 0a 89 6b 97  |o....B.,.#m...k.|
00000110  2c 25 e9 f6 b1 84 b3 ff  b3 ab 43 25 ad 67 c8 40  |,%........C%.g.@|
00000120  fc fc 2e 49 d7 ef 27 2b  30 75 9d 60 f8 93 a4 46  |...I..'+0u.`...F|
00000130  a2 df f9 6a 10 c7 a3 43  13 2d e2 8b eb 14 3d 69  |...j...C.-....=i|
00000140  ba bf ac fe 2f d7 d1 fb  16 a1 7c 41 4b 6e 07 a5  |..../.....|AKn..|
00000150  81 4d 60 52 96 ef 97 c8  e5 7e 43 ad b2 86 0c 0a  |.M`R.....~C.....|
00000160  50 4b 0e 25 57 43 bd ec  93 88 99 ef 2e 7b 6a d7  |PK.%WC.......{j.|
00000170  16 6e 0e cf 65 8b da 6b  0e 5c 7b a7 93 92 f3 2d  |.n..e..k.\{....-|
00000180  e6 06 d4 75 ac 21 e6 cb  be b4 61 0c 0d 0c f6 25  |...u.!....a....%|
00000190  3c d6 a4 ab c5 69 cd 6b  4f 5a de cc ec 64 4d 7f  |<....i.kOZ...dM.|
000001a0  d6 36 d2 71 ee 04 68 bd  c9 be 81 2f 63 ba d8 35  |.6.q..h..../c..5|
000001b0  9c 44 57 9f d3 ce 3d db  99 54 80 70 89 19 00 fe  |.DW...=..T.p....|
000001c0  ff ff 06 fe ff ff 02 90  63 06 00 d8 02 00 00 fe  |........c.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 88 63 06 00 00  |............c...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```Can anybody help? I'm tearing my hair out!

---

### Post by hhh on 2011-07-26
What happens if in etc/default/grub you comment out (put a # symbol before each line so the computer ignores it) the lines...```
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
```... and then in a terminal run...```
sudo update-grub
```... and reboot?

---

### Post by Perplexed Pat on 2011-07-26
Nothing. It's still the same.

pat@pat:~$ sudo update-grub
[sudo] password for pat: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
pat@pat:~$

---

### Post by hhh on 2011-07-26
Try deleting those 2 lines entirely. According to your post, update-grub is finding Windows, so something is making grub not display. More info here...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I won't be at a computer till tomorrow, sorry. Hopefully someone else will take over.

---

### Post by Perplexed Pat on 2011-07-26
Cheers hhh.

---

### Post by thefasterblueone on 2011-07-26
Boot off a Windows XP disc, get to the Console ( Watch for a "Press any key to boot from CD"... message ) and type the following commands:

```
fixmbr
```

```
fixboot
```

---

### Post by Perplexed Pat on 2011-07-26
Thanks for your suggestions. I solved it. Believe it or not it was because my F6 key was stuck down! I just need a new keyboard. :oops:

---

