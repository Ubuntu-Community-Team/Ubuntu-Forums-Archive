---
title: "Problem with dual boot and booting from CD"
date: 2011-03-15
forum: General Help
---

### Post by charliebarter on 2011-03-15
So I recently reinstalled XP onto my system, and after that when I booted it would show me the GRUB boot options for about 0.2 seconds and I couldn't change the option and then it would boot straight into Ubuntu.

I found a way around this by booting my ultimate boot CD first, before the hard drive boots and then asking to boot from Drive 1 which gave me the GRUB options for 10 seconds and allowed me to boot into windows.

However, since installing SP3 for XP Home Edition and restarting my computer no longer boots into the ultimate boot cd instead it just skips over searching for a CD and boots Ubuntu: Again showing me the GRUB options for 0.2 seconds and then booting Ubuntu.

I have tried using my XP restore CD and this does not boot either it skips straight to booting Ubuntu. 

I have also tried entering into the BIOS or just the boot order settings to check that CD is being booted before hard drive. However, I CANNOT GET INTO MY BIOS. Whenever I click F12 it gives me a screen saying it is loading into options but then starts to boot Ubuntu rather than loading the BIOS. In addition on the initial page the normal options press f2 for boot order and f12 for BIOS are not seen anymore.

This is very frustrating as I cannot even reinstall XP again because boot CDs are not run and I cannot enter my BIOS.

Here are the results of Fdisk -l

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4b3d4b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        9645    77459456    c  W95 FAT32 (LBA)
/dev/sda3            9645       12148    20108289    5  Extended
/dev/sda4           12149       12161      104422+  83  Linux
/dev/sda5   *        9645       12039    19225600   83  Linux
/dev/sda6           12039       12148      881664   82  Linux swap / Solaris

```And the results of bootinfo.sh

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 161428760 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

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

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/lilo.conf /boot/map

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              18,432   154,937,343   154,918,912   c W95 FAT32 (LBA)
/dev/sda3         154,939,390   195,155,967    40,216,578   5 Extended
/dev/sda5    *    154,939,392   193,390,591    38,451,200  83 Linux
/dev/sda6         193,392,640   195,155,967     1,763,328  82 Linux swap / Solaris
/dev/sda4         195,157,620   195,366,464       208,845  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        320D-180E                              vfat       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda4        650b7c39-8e53-48b3-bf57-88b0b86dff43   ext2                                     
/dev/sda5        11ce0c65-c350-4d67-89be-b4ade6cb0a99   ext4                                     
/dev/sda6        172e6bf0-46a3-465f-928d-548ce279180e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sr0         /media/UBCDBASIC         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 11ce0c65-c350-4d67-89be-b4ade6cb0a99
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 11ce0c65-c350-4d67-89be-b4ade6cb0a99
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 11ce0c65-c350-4d67-89be-b4ade6cb0a99
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=11ce0c65-c350-4d67-89be-b4ade6cb0a99 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 11ce0c65-c350-4d67-89be-b4ade6cb0a99
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=11ce0c65-c350-4d67-89be-b4ade6cb0a99 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 11ce0c65-c350-4d67-89be-b4ade6cb0a99
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=11ce0c65-c350-4d67-89be-b4ade6cb0a99 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 11ce0c65-c350-4d67-89be-b4ade6cb0a99
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=11ce0c65-c350-4d67-89be-b4ade6cb0a99 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 11ce0c65-c350-4d67-89be-b4ade6cb0a99
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 11ce0c65-c350-4d67-89be-b4ade6cb0a99
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 320d-180e
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
UUID=11ce0c65-c350-4d67-89be-b4ade6cb0a99 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=172e6bf0-46a3-465f-928d-548ce279180e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  82.6GB: boot/grub/core.img
  96.9GB: boot/grub/grub.cfg
  81.0GB: boot/initrd.img-2.6.35-22-generic
  81.1GB: boot/initrd.img-2.6.35-27-generic
  81.6GB: boot/vmlinuz-2.6.35-22-generic
  81.6GB: boot/vmlinuz-2.6.35-27-generic
  81.1GB: initrd.img
  81.0GB: initrd.img.old
  81.6GB: vmlinuz
  81.6GB: vmlinuz.old

============================= sda4/etc/lilo.conf: =============================

boot=/dev/hda4
map=/boot/map
install=/boot/boot.b
lba32
default=icava

image=/boot/kernel
    label=icava
    root=/dev/hda4
    initrd=/boot/initrd.img
    read-only
    append="quiet video=vesa:mtrr"
    vga=0x315

=================== sda4: Location of files loaded by Grub: ===================


  99.9GB: boot/initrd.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  77 67 37 af 55 c0 92 7f  b6 06 e7 b9 3a 9d f7 46  |wg7.U.......:..F|
00000010  2d 59 65 93 a2 d1 5c 22  a2 b2 20 68 a2 22 1c 86  |-Ye...\".. h."..|
00000020  00 d2 da ad 8b 55 35 ab  cd 2e 2e 85 9a 0c 81 f3  |.....U5.........|
00000030  f0 97 c8 38 de 75 5b 3a  05 ca 7b aa 4a 76 2f 74  |...8.u[:..{.Jv/t|
00000040  33 18 b2 78 4b 2d 97 c8  30 46 eb 3c 61 80 20 71  |3..xK-..0F.<a. q|
00000050  b8 8e 12 2f a0 ac 43 b8  b0 6d 1e 1e 92 66 ad b6  |.../..C..m...f..|
00000060  35 e0 ef 96 86 ca e2 eb  e7 82 17 b9 66 fd ab b6  |5...........f...|
00000070  63 78 fb 87 05 57 56 6f  10 9f 5c aa 5d 0c 37 40  |cx...WVo..\.].7@|
00000080  fa 9c d9 17 17 4b 50 e4  1e 67 f6 a4 59 5c 60 fe  |.....KP..g..Y\`.|
00000090  7a eb 55 f7 f2 77 b3 29  32 19 93 a8 f8 33 da 68  |z.U..w.)2....3.h|
000000a0  d0 57 25 7b c6 b3 65 4e  cd b6 31 80 0c 58 f7 d6  |.W%{..eN..1..X..|
000000b0  24 db 4b 67 35 aa 17 16  39 fb d9 14 9b 3b 86 24  |$.Kg5...9....;.$|
000000c0  5a 75 b6 74 dc 79 d6 94  e2 8c 6c 59 b6 2d 9c 21  |Zu.t.y....lY.-.!|
000000d0  0a 95 6d 2d 94 86 51 21  49 00 0d 1a 39 34 a2 ee  |..m-..Q!I...94..|
000000e0  c8 bd 55 ef 54 92 58 9b  4e 95 7b 9a 3e 46 f4 4c  |..U.T.X.N.{.>F.L|
000000f0  66 4a 03 5b 25 4f af 38  b6 20 9b b5 9f aa b1 08  |fJ.[%O.8. ......|
00000100  ec a9 7e 1c 8a eb ae f2  21 94 9a 82 53 b7 50 8d  |..~.....!...S.P.|
00000110  5a dd c1 28 84 b8 99 e5  48 0a 9f 6d 2d 16 3a 17  |Z..(....H..m-.:.|
00000120  d3 fe 18 71 7d 0e c5 28  b5 75 e3 a6 3f 79 65 d7  |...q}..(.u..?ye.|
00000130  a0 fc eb 45 7f c3 d8 8e  82 67 7a 9f 3d cd d6 f4  |...E.....gz.=...|
00000140  57 d5 ca c8 9b 4d 8d b0  b2 e1 3d 1d 5e f3 a7 2d  |W....M....=.^..-|
00000150  7e 92 98 03 c8 44 f3 03  97 91 bf 2b 0b 30 e3 b9  |~....D.....+.0..|
00000160  3e 16 be 75 fe 61 1f 4f  6d ee 51 7d 65 72 45 89  |>..u.a.Om.Q}erE.|
00000170  b1 7d b4 cf 94 49 1a ba  75 43 3c 0f 8b 18 92 b8  |.}...I..uC<.....|
00000180  0e ad 9f f4 f5 6d 63 ad  32 33 7a 6a f3 1e 11 a6  |.....mc.23zj....|
00000190  42 94 c1 b7 0b ec e2 70  96 b4 85 44 65 a1 55 82  |B......p...De.U.|
000001a0  80 05 97 6e 4d 28 97 72  ad 76 81 17 04 fe 48 df  |...nM(.r.v....H.|
000001b0  a9 be 5a 87 42 bf fb b4  78 fd 37 5c 91 b1 80 fe  |..Z.B...x.7\....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 4a 02 00 fe  |............J...|
000001d0  ff ff 05 fe ff ff 02 b8  4a 02 00 f0 1a 00 00 00  |........J.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda4

00000000  fa eb 70 6c 62 61 4c 49  4c 4f 01 00 15 04 ff ff  |..plbaLILO......|
00000010  00 00 00 00 00 f8 bd 00  ff 13 b0 a3 0b 00 14 b0  |................|
00000020  a3 0b fe 13 b0 a3 0b 00  00 00 00 00 00 00 00 02  |................|
00000030  14 b0 a3 0b ab 60 b0 a2  0b ac 60 b0 a2 0b ad 60  |.....`....`....`|
00000040  b0 a2 0b ae 60 b0 a2 0b  af 60 b0 a2 0b b0 60 b0  |....`....`....`.|
00000050  a2 0b b1 60 b0 a2 0b b2  60 b0 a2 0b 00 00 00 00  |...`....`.......|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 b8 c0 07 8e d8  8c 06 6e 00 89 36 6c 00  |..........n..6l.|
00000080  89 1e 70 00 88 16 72 00  b8 00 9a 8e c0 b9 00 01  |..p...r.........|
00000090  29 f6 29 ff fc f3 a5 ea  9c 00 00 9a 8e d8 b8 00  |).).............|
000000a0  90 8e d0 bc 00 b0 fb b0  0d e8 69 00 b0 0a e8 64  |..........i....d|
000000b0  00 b0 4c e8 5f 00 be 34  00 68 00 0b 07 31 db ad  |..L._..4.h...1..|
000000c0  91 ac a8 60 75 0f 4e ad  89 c2 09 c8 74 1c ac b4  |...`u.N.....t...|
000000d0  02 cd 13 eb 0e 88 c2 ad  f6 c2 20 75 02 30 e4 97  |.......... u.0..|
000000e0  e8 39 00 72 0f 80 c7 02  eb d5 b0 49 e8 26 00 ea  |.9.r.......I.&..|
000000f0  00 00 00 0b b0 20 e8 1c  00 e8 06 00 31 c0 cd 13  |..... ......1...|
00000100  eb b4 c1 c0 04 e8 03 00  c1 c0 04 24 0f 04 30 3c  |...........$..0<|
00000110  3a 72 02 04 07 50 30 ff  b4 0e 58 c3 56 51 53 88  |:r...P0...X.VQS.|
00000120  d3 80 e2 8f f6 c3 40 75  33 bb aa 55 b8 00 41 cd  |......@u3..U..A.|
00000130  13 72 29 81 fb 55 aa 75  23 f6 c1 01 74 1e 5b 59  |.r)..U.u#...t.[Y|
00000140  1e 31 f6 56 56 57 51 06  53 6a 01 6a 10 89 e6 16  |.1.VVWQ.Sj.j....|
00000150  1f b8 00 42 cd 13 8d 64  10 1f eb 44 5b 59 53 52  |...B...d...D[YSR|
00000160  57 51 06 b4 08 cd 13 07  72 38 51 c0 e9 06 86 e9  |WQ......r8Q.....|
00000170  89 cf 59 88 f0 fe c0 80  e1 3f f6 e1 96 58 5a 39  |..Y......?...XZ9|
00000180  f2 73 23 f7 f6 39 f8 77  1d c0 e4 06 86 e0 92 f6  |.s#..9.w........|
00000190  f1 fe c4 00 e2 89 d1 5a  5b 86 f0 b8 01 02 cd 13  |.......Z[.......|
000001a0  5e c3 59 5f eb 02 b4 40  5a 5b f9 eb f3 00 00 00  |^.Y_...@Z[......|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Any ideas about how I can get back to being able to booting to XP?

---

### Post by charliebarter on 2011-03-15
I have even tried changing my default boot in grub to the windows boot, still boots into ubuntu

---

### Post by dabl on 2011-03-15
Two things:

1. BIOS entry has nothing to do with installed operating systems.  You might have a broken computer.  Better review the computer's user manual, looking at things like removing the CMOS battery for a period of time, so BIOS can revert to default setup.

2. In Ubuntu, have you run ```
sudo update-grub
``` anything lately?  It should detect Win XP and adjust /boot/grub/grub.cfg to enable booting.

---

### Post by dragonfly41 on 2011-03-15
Re: "Any ideas about how I can get back to being able to booting to XP?"

I'm in a similar situation where my Vista OS on my Dell laptop has crashed although I can get into Ubuntu (demo mode - not yet full installation).  I can't use CD-RW devices for some reason - inserted disks not recognised for some reason - so I'm using USB devices for now.   I'm transferring my Vista files onto USB drive before going through the next stage of full Ubuntu installation (which will wipe my Vista files).

I hit F11 to see the two dual boot options (is it Grub menu):-

Windows Vista
Ubuntu

In some systems(such as XP) I believe that it might be F10.

And then I go into Esc > Demo mode .. to use Ubuntu in Demo mode.

In fact I can see my all Windows files in Ubuntu File System > isodevice .. but I wouldn't know what to hack to get my Vista to boot up again.

---

### Post by charliebarter on 2011-03-15
thanks, I have run

```

sudo update -grub

```I understand that the bios is not directly related to the operating systems installed, but I can't even completely format my hardrive if I cannot boot into a bootable CD rom, but I guess the two problems, 

GRUB only lasting for 0.2 seconds and loading ubuntu even when I can see that the windows boot is highlighted;

and not being able to open BIOS settings or boot to a bootable CD 

Which must be separate.

---

### Post by dabl on 2011-03-15
In the file /etc/default/grub the grub menu timeout delay is set on the line:

GRUB_TIMEOUT=10

I think 10 seconds is the default, but maybe yours is set to 2.  You can edit that file with your text editor, with a "sudo" prefix.

---

