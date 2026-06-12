---
title: "Keyboard not working since last update"
date: 2010-12-24
forum: General Help
---

### Post by nosmokenofire on 2010-12-24
When I boot up a few things are different than before the last update:

grub no longer does the 10 second countdown
the ubuntu splash screen has changed to some wierd text version "Ubuntu 10.10"
when the boot is finished nothing works on my laptop (keyboard, mouse, integrated touchpad mouse thing...). I am able to get the mouse to work by unpluging it from the usb port and plugging it back in.

applications seem to work fine, (thunderbird, firefox, etc) the ony ploblem is that I have no way of typing anything... Also i have a keyboard icon that was never there before that puts my keyboard in USA mode (it has always been set to french since my install.

PLease help if you can as I cannot use Ubuntu at all...

I have a dual boot vista/maverick on an Acer Aspire 5100 laptop.

Many thanks.

---

### Post by nosmokenofire on 2010-12-25
I ran a boot_info_script and got this:

             >   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,370,234    16,370,172  12 Compaq diagnostics
/dev/sda2    *     16,370,235    86,654,609    70,284,375   6 FAT16
/dev/sda3          86,654,610   124,148,796    37,494,187   7 HPFS/NTFS
/dev/sda4         124,149,758   156,301,311    32,151,554   5 Extended
/dev/sda5         124,149,760   154,859,519    30,709,760  83 Linux
/dev/sda6         154,861,568   156,301,311     1,439,744  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2097 MB, 2097152000 bytes
56 heads, 55 sectors/track, 1329 cylinders, total 4096000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             64     4,095,999     4,095,936   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8A408E8916D9B5D2                       ntfs       PQSERVICE                     
/dev/sda2        64700DE6700DBFB2                       ntfs       ACER                          
/dev/sda3        BA78567378562DFF                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        af4d1611-2505-4ed4-8d83-798ae5d124b5   ext4                                     
/dev/sda6        d41e7ce7-9608-4a0a-a7cd-14d1c99194da   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A2A0-5EB1                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=af4d1611-2505-4ed4-8d83-798ae5d124b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=af4d1611-2505-4ed4-8d83-798ae5d124b5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=af4d1611-2505-4ed4-8d83-798ae5d124b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=af4d1611-2505-4ed4-8d83-798ae5d124b5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=af4d1611-2505-4ed4-8d83-798ae5d124b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=af4d1611-2505-4ed4-8d83-798ae5d124b5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set af4d1611-2505-4ed4-8d83-798ae5d124b5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8a408e8916d9b5d2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 64700de6700dbfb2
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=af4d1611-2505-4ed4-8d83-798ae5d124b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d41e7ce7-9608-4a0a-a7cd-14d1c99194da none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  74.5GB: boot/grub/core.img
  73.4GB: boot/grub/grub.cfg
  77.2GB: boot/initrd.img-2.6.32-25-generic
  78.0GB: boot/initrd.img-2.6.35-22-generic
  77.1GB: boot/initrd.img-2.6.35-23-generic
  75.6GB: boot/vmlinuz-2.6.32-25-generic
  74.5GB: boot/vmlinuz-2.6.35-22-generic
  78.0GB: boot/vmlinuz-2.6.35-23-generic
  78.3GB: boot/vmlinuz-2.6.35-24-generic
  77.1GB: initrd.img
  78.0GB: initrd.img.old
  78.0GB: vmlinuz
  74.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  27 e0 85 37 4a 29 1d bc  c1 64 85 ab 18 4e 66 0d  |'..7J)...d...Nf.|
00000010  42 36 49 d9 c4 63 9b 6b  1f 81 6b 15 ed d3 30 62  |B6I..c.k..k...0b|
00000020  10 c8 53 08 59 8c 2c 2f  a1 80 e6 ae 35 0b 79 d6  |..S.Y.,/....5.y.|
00000030  cd d8 34 13 b3 63 3c e0  ca 6c 3c 2e 70 52 a2 d5  |..4..c<..l<.pR..|
00000040  59 0b 7c 94 4a 4d 5f c6  87 71 9a 92 38 ce 35 cd  |Y.|.JM_..q..8.5.|
00000050  4b be b2 88 4c 22 ab 72  20 0e 5a b0 19 67 1a f5  |K...L".r .Z..g..|
00000060  88 cc a5 c0 a4 1c 86 89  41 cc 15 77 d2 da df b5  |........A..w....|
00000070  f8 7a 2b 99 2f 76 a8 09  ea ad be 7c 64 85 d4 1b  |.z+./v.....|d...|
00000080  ae 3c 6b 39 f8 0d 11 0a  2c f9 66 1f 02 b3 13 d1  |.<k9....,.f.....|
00000090  6b d3 86 e0 d6 c2 eb 9f  36 fe 9a 2c 32 b2 46 1d  |k.......6..,2.F.|
000000a0  a8 bf 3a 02 00 98 ea 14  d9 f6 38 f5 ea 29 5f 28  |..:.......8..)_(|
000000b0  fe 55 d7 fe 73 b4 fd 36  4b c4 50 69 55 43 ed f3  |.U..s..6K.PiUC..|
000000c0  76 05 b0 32 bf 80 41 70  ee 66 1b cf bd 72 e7 cf  |v..2..Ap.f...r..|
000000d0  57 e3 13 82 13 28 19 5b  21 56 60 99 0c ea a3 a7  |W....(.[!V`.....|
000000e0  85 2e 8e c3 ed eb 41 5a  88 c7 b7 5c 9a 85 f4 af  |......AZ...\....|
000000f0  df 90 eb 29 cd 44 49 0c  2a 0d 50 21 fb 84 b0 c7  |...).DI.*.P!....|
00000100  5d ba 63 71 f3 7d 7c d9  e7 fb c9 8c 1d c2 4c 4e  |].cq.}|.......LN|
00000110  4a 17 30 9d ab a5 7d c4  bd b2 d2 ea ed 98 22 33  |J.0...}......."3|
00000120  a2 14 87 ba 45 27 14 11  f5 27 af 4b 7d df 43 32  |....E'...'.K}.C2|
00000130  75 77 30 05 a8 a0 c0 a9  3c 3d 53 2a 88 5a a2 a3  |uw0.....<=S*.Z..|
00000140  50 58 fa 8c bc 62 3b 66  75 c9 74 ab 95 32 ef 46  |PX...b;fu.t..2.F|
00000150  64 fd 34 9e 5b af ce 4e  07 67 d3 00 71 71 56 92  |d.4.[..N.g..qqV.|
00000160  09 fd f9 e8 cb b7 06 31  71 d0 4e 93 3e a2 63 48  |.......1q.N.>.cH|
00000170  50 7b 12 e0 ea 45 ad fd  cc e3 fd 68 9a 05 df c0  |P{...E.....h....|
00000180  d8 40 7e 02 04 f3 a2 19  58 e0 d0 b6 e1 d0 d0 45  |.@~.....X......E|
00000190  a0 8b 20 e2 18 aa a3 ec  26 82 7b c5 80 10 1e b4  |.. .....&.{.....|
000001a0  a5 ac 9a 74 f6 30 b5 5d  f5 18 f0 eb 24 fb f8 62  |...t.0.]....$..b|
000001b0  95 d9 14 da 18 09 9b 37  90 55 87 30 2f 04 00 fe  |.......7.U.0/...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 98 d4 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 98  d4 01 00 00 16 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200thanks for any help anyone can offer.

---

### Post by nosmokenofire on 2010-12-26
I've marked this as solved. All I did was reinstall from CD. I installed Lucid, which I now intend to stick to until the next LTS version comes out.

Bye...

---

