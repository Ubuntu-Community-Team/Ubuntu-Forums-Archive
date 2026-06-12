---
title: "target file system doesnt have requested /sbin/init"
date: 2011-07-21
forum: General Help
---

### Post by rahulkale on 2011-07-21
I tried booting to Ubuntu 11.04 like a regular day and boom got this error message....

containing two lines... 

> 

target file system doesnt have requested /sbin/init

Run-init: /bin/sh: no such file or directory



I am also attaching the bootinfo script code Result :

Please help..

Found it on net that need to run a command named 

> 

Sudo fsck /dev/sda* where * is the bootable drive... but this doesnt work...

It says an Error as 

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1



 


```
  

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

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
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 60868 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    21,511,034    21,510,972   7 NTFS / exFAT / HPFS
/dev/sda2          21,511,035    59,392,304    37,881,270   7 NTFS / exFAT / HPFS
/dev/sda3          59,392,305    97,273,574    37,881,270   7 NTFS / exFAT / HPFS
/dev/sda4          97,273,636   156,301,311    59,027,676   f W95 Extended (LBA)
/dev/sda5          97,273,638   135,154,844    37,881,207   7 NTFS / exFAT / HPFS
/dev/sda6         135,155,712   154,224,639    19,068,928  83 Linux
/dev/sda7         154,226,688   156,301,311     2,074,624  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,633,407    15,633,345   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       4f88249d-7bc7-cd41-9e08-1bcd6f6ac183   ext2       casper-rw
/dev/sda1        34F49436F493F7F6                       ntfs       
/dev/sda2        16D0D54DD0D533A9                       ntfs       New Volume
/dev/sda3        FAD00D6AD00D2F07                       ntfs       New Volume
/dev/sda5        DA8835E08835BBB7                       ntfs       New Volume
/dev/sda6        85ee7e32-a792-4eab-8fdd-382ee2fce363   ext4       
/dev/sda7        85833c15-494b-4941-b609-1d49f426d06f   swap       
/dev/sdb1        11FC-1953                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; This boot.ini was automatically generated by NeoSmart Technologies' BootGrabber.exe 
; Use EasyBCD from http://neosmart.net/dl.php?id=1 to manage your bootloader 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP on C:\" /fastdetect 
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
set default="6"
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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 85ee7e32-a792-4eab-8fdd-382ee2fce363
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 85ee7e32-a792-4eab-8fdd-382ee2fce363
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 85ee7e32-a792-4eab-8fdd-382ee2fce363
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=85ee7e32-a792-4eab-8fdd-382ee2fce363 ro  splash  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 85ee7e32-a792-4eab-8fdd-382ee2fce363
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=85ee7e32-a792-4eab-8fdd-382ee2fce363 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 85ee7e32-a792-4eab-8fdd-382ee2fce363
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=85ee7e32-a792-4eab-8fdd-382ee2fce363 ro  splash  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 85ee7e32-a792-4eab-8fdd-382ee2fce363
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=85ee7e32-a792-4eab-8fdd-382ee2fce363 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 85ee7e32-a792-4eab-8fdd-382ee2fce363
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 85ee7e32-a792-4eab-8fdd-382ee2fce363
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 34F49436F493F7F6
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
# / was on /dev/sda6 during installation
UUID=85ee7e32-a792-4eab-8fdd-382ee2fce363 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=85833c15-494b-4941-b609-1d49f426d06f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  65.538642883 = 70.371581952   boot/grub/core.img                             1
  70.757667542 = 75.975467008   boot/grub/grub.cfg                             1
  67.357669830 = 72.324747264   boot/initrd.img-2.6.38-10-generic              1
  66.009765625 = 70.877446144   boot/initrd.img-2.6.38-8-generic               2
  66.162418365 = 71.041355776   boot/vmlinuz-2.6.38-10-generic                 1
  65.537830353 = 70.370709504   boot/vmlinuz-2.6.38-8-generic                  1
  67.357669830 = 72.324747264   initrd.img                                     1
  66.009765625 = 70.877446144   initrd.img.old                                 2
  66.162418365 = 71.041355776   vmlinuz                                        1
  65.537830353 = 70.370709504   vmlinuz.old                                    1

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

00000000  70 ef 72 b5 66 95 1a 4c  30 5a a5 27 3c 5f 9f 12  |p.r.f..L0Z.'<_..|
00000010  b3 08 7d 1c 01 fe f2 a1  e4 d7 26 0c 07 b1 46 4c  |..}.......&...FL|
00000020  3a 5c 25 fb 8f 2f 92 35  1d 47 f3 0d a5 20 59 51  |:\%../.5.G... YQ|
00000030  77 3c 7b 1b 23 5e 91 a2  40 91 dd 80 c6 5c ed a8  |w<{.#^..@....\..|
00000040  82 5c 7d 8f 45 ef b7 bd  f5 b7 ba be b2 0e 2d 4b  |.\}.E.........-K|
00000050  32 5c 18 c3 4c 53 dd d6  c1 88 d8 99 f7 57 d5 be  |2\..LS.......W..|
00000060  1d 72 77 d8 69 01 9d 50  45 66 1e 7b 75 75 73 bb  |.rw.i..PEf.{uus.|
00000070  ee e3 36 07 55 82 92 01  57 83 c0 40 92 0f 01 fd  |..6.U...W..@....|
00000080  68 30 92 0f 03 01 48 30  06 00 78 97 e0 61 1f ea  |h0....H0..x..a..|
00000090  81 08 7c 0c 97 e3 87 01  88 46 0f 01 06 18 3c 07  |..|......F....<.|
000000a0  ef 20 df 03 e0 1e 01 80  c3 ef 50 66 81 87 65 e2  |. ........Pf..e.|
000000b0  e7 a6 0a 02 97 f5 4f ed  ad de d4 a6 43 28 cf c8  |......O.....C(..|
000000c0  e4 34 f0 22 a1 00 62 b7  7d e9 80 18 0a 8f 7e 7f  |.4."..b.}.....~.|
000000d0  e0 c1 90 33 84 90 60 c8  33 b7 b4 e3 50 cf a8 03  |...3..`.3...P...|
000000e0  c0 41 fa e4 e0 b4 70 30  05 fd c3 f3 29 c1 d5 fc  |.A....p0....)...|
000000f0  e4 a7 44 b1 f8 ee 1c 2e  94 f2 79 e1 eb 58 e2 e9  |..D.......y..X..|
00000100  4f 39 34 a7 8f 97 66 d6  ce 7b c0 c6 e1 94 c4 07  |O94...f..{......|
00000110  40 25 43 fd 7a f8 69 b3  02 13 e7 45 80 c0 2d f3  |@%C.z.i....E..-.|
00000120  08 d0 21 d3 6b 90 a7 23  5e 09 8a f4 5e fb ef be  |..!.k..#^...^...|
00000130  ee b3 c3 ef 6d 62 a6 da  e9 a7 a7 df 72 bd bb 68  |....mb......r..h|
00000140  77 37 ee 3a c3 67 9f 73  be fd dd e8 29 80 a0 70  |w7.:.g.s....)..p|
00000150  78 08 14 41 e0 20 5f aa  01 82 12 96 21 78 67 55  |x..A. _.....!xgU|
00000160  51 ef ef ea c2 80 78 08  14 41 e0 20 53 f0 3c 14  |Q.....x..A. S.<.|
00000170  06 25 ca ab 7f 57 7e 0c  40 08 4d 90 2b 56 0c 6f  |.%...W~.@.M.+V.o|
00000180  ca 81 8d 23 21 12 99 7a  b0 54 02 9c 98 01 42 28  |...#!..z.T....B(|
00000190  30 05 7c bf fd 3c a0 d0  fa 9b 4c 40 0e 3e f1 b1  |0.|..<....L@.>..|
000001a0  f8 05 78 02 8b c3 20 c1  28 a5 7a b5 f5 ed 81 a4  |..x... .(.z.....|
000001b0  e4 e0 1a a8 f9 7c ba 19  47 17 b9 3a 1f d3 00 01  |.....|..G..:....|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 77 05 42 02 00 fe  |..........w.B...|
000001d0  ff ff 05 fe ff ff 79 05  42 02 63 fb 22 01 00 00  |......y.B.c."...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected



```

---

### Post by rahulkale on 2011-07-21
I tried Running 

sudo fsck /dev/sda6

Since it contains the grub files.... it comes out clean with no errors...
But same error comes againg on startup... 

:(

---

