---
title: "error: so such device (after restore from backup)"
date: 2011-09-05
forum: General Help
---

### Post by bradburns on 2011-09-05
Hi friends,

Thanks for reading my post! :)

I have 2 old dell poweredge 1850 1U servers that are exactly the same in spec running ubuntu 11.04 server edition. I'm going to make one of them my dev machine at my house and the other my live machine in a co-location datacenter for a few websites. 

The idea is, if I royally mess-up my dev installation, I want to be able to pull one of the backups (an image or total partition archives) from my live server and restore it to my dev server... or visa versa.

I found this post: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) which describes how to archive your machine using tar. Great! However, when i restore it from the live machine to the dev machine, I get:

```
error: no such device: [hex code].
error: hd1 cannot get C/H/S values.
error: you need to lead the kernel first.
```

I'm open to ideas on a better way to accomplish this. It sounds to me as if I copied something that does not agree with a serial number of a piece of hardware, (hex code?). I'm pretty new, if you cant tell.

Your thoughts are appreciated!:D

edit: changed HTML box to CODE box

---

### Post by drs305 on 2011-09-05
Hi bradburns

Welcome to the Ubuntu Forums.

The easiest way for us to help is to see the information about your boot files. You can provide it by booting the Ubuntu LiveCD and downloading/extracting/running the boot info script from the following site. 

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

It will produce a file called RESULTS.txt. Post the contents here, between 'code' tags. You generate them while typing the post by pressing the # icon in the post's menu bar.

I'm about to log off for the night but someone should be around to help you out or I'll check back tomorrow.

---

### Post by bradburns on 2011-09-06
Hi! Thanks for the quick reply.

Here is the code:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30558 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

Popeye-root': __________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

Popeye-swap_1': ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 146.7 GB, 146695782400 bytes
255 heads, 63 sectors/track, 17834 cylinders, total 286515200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   286,513,151   286,011,394   5 Extended
/dev/sda5             501,760   286,513,151   286,011,392  8e Linux LVM


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,843,814     7,843,752   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/Popeye-root cf35c52c-7ce2-4740-95cb-4d7d4256b341   ext4       
/dev/mapper/Popeye-swap_1 c650dec8-bad4-4d08-898e-893951c82a10   swap       
/dev/sda1        6b6a3156-9535-46a9-b3aa-73e93719dae3   ext2       
/dev/sda5        QxHXau-IlsP-4QqA-9DDd-6Eaf-Y84U-VQNpFM LVM2_member 
/dev/sdb1        1200-3264                              vfat       PENDRIVE

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
Popeye-root
Popeye-swap_1
control

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/Bluto-root /                        ext4       (rw,errors=remount-ro)


============================= sda1/grub/grub.cfg: ==============================

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

insmod lvm
insmod part_msdos
insmod ext2
set root='(Bluto-root)'
search --no-floppy --fs-uuid --set=root d5d2d2ca-d7f2-4b50-b2cc-3c15c127e1de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root f3a91e3c-acc9-429f-8a37-42907f6e3ec2
set locale_dir=($root)/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
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
menuentry 'Ubuntu, with Linux 2.6.38-8-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f3a91e3c-acc9-429f-8a37-42907f6e3ec2
    linux    /vmlinuz-2.6.38-8-server root=/dev/mapper/Bluto-root ro   quiet
    initrd    /initrd.img-2.6.38-8-server
}
menuentry 'Ubuntu, with Linux 2.6.38-8-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f3a91e3c-acc9-429f-8a37-42907f6e3ec2
    echo    'Loading Linux 2.6.38-8-server ...'
    linux    /vmlinuz-2.6.38-8-server root=/dev/mapper/Bluto-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f3a91e3c-acc9-429f-8a37-42907f6e3ec2
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root f3a91e3c-acc9-429f-8a37-42907f6e3ec2
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.144991875 = 0.155683840    grub/core.img                                  2
   0.144996643 = 0.155688960    grub/grub.cfg                                  1
   0.040696144 = 0.043697152    initrd.img-2.6.38-8-server                    59
   0.008262634 = 0.008871936    vmlinuz-2.6.38-8-server                       19

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Install Ubuntu Server" {
    set gfxpayload=keep
    linux    /install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed quiet --
    initrd    /install/initrd.gz
}
menuentry "Install in expert mode" {
    set gfxpayload=keep
    linux    /install/vmlinuz  file=/cdrom/preseed/ubuntu-server.seed priority=low --
    initrd    /install/initrd.gz
}
menuentry "Install Ubuntu Enterprise Cloud" {
    set gfxpayload=keep
    linux    /install/vmlinuz  file=/cdrom/preseed/cloud.seed quiet --
    initrd    /install/initrd.gz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /install/vmlinuz  MENU=/bin/cdrom-checker-menu quiet --
    initrd    /install/initrd.gz
}
menuentry "Rescue a broken system" {
    set gfxpayload=keep
    linux    /install/vmlinuz  rescue/enable=true --
    initrd    /install/initrd.gz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 0
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

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

Unknown BootLoader on sda2

00000000  f6 41 98 c0 16 22 e4 65  94 63 13 20 47 70 8c 7c  |.A...".e.c. Gp.||
00000010  82 64 27 6e b8 b2 e3 97  81 c6 40 ff 5a 55 bb c3  |.d'n......@.ZU..|
00000020  81 87 d9 8b b8 c3 f5 cd  48 c5 52 9e 8f 52 24 d7  |........H.R..R$.|
00000030  62 45 f8 47 89 18 12 e1  1f 1e 3d 0d b1 ef b1 bd  |bE.G......=.....|
00000040  3f 65 1f 11 6a 30 18 d4  d8 47 84 b7 b9 a1 d6 43  |?e..j0...G.....C|
00000050  6a c9 93 a0 7c 21 6a 10  52 07 e9 a1 3f 16 10 c4  |j...|!j.R...?...|
00000060  28 fd 30 75 49 9a 1c 55  88 72 54 be 9d a6 90 85  |(.0uI..U.rT.....|
00000070  b4 15 a2 9e 87 ab 34 8b  35 0a 9d 16 10 c4 2f 5f  |......4.5...../_|
00000080  2c 11 93 27 7a f8 dd 13  df bc 19 13 e4 83 56 a8  |,..'z.........V.|
00000090  96 97 6b 85 07 52 bc 64  cb 18 88 f3 6a 59 66 af  |..k..R.d....jYf.|
000000a0  9e 8e f3 26 2f 5d 48 8a  17 55 ab f9 fa 64 4b 34  |...&/]H..U...dK4|
000000b0  bf 36 6a db 50 fd 06 be  54 a1 47 32 1a 2e 89 da  |.6j.P...T.G2....|
000000c0  a7 bc b8 71 07 d7 e6 59  da e4 bc 2b 1d 33 ef 70  |...q...Y...+.3.p|
000000d0  97 74 04 4d 81 b9 2b 03  5c 47 30 12 78 65 a1 f6  |.t.M..+.\G0.xe..|
000000e0  81 3a 02 f7 8c c1 2c 57  00 8a eb 32 a1 c1 5c c6  |.:....,W...2..\.|
000000f0  01 79 0d 63 cf 86 50 8d  bf 13 e7 ad cb 71 05 d4  |.y.c..P......q..|
00000100  1d 9b 02 9c 61 6f 42 7d  ea 69 b2 05 54 06 04 81  |....aoB}.i..T...|
00000110  01 4e a0 e0 cc 31 c3 81  7d 14 67 16 f6 31 16 70  |.N...1..}.g..1.p|
00000120  ba 08 b9 68 93 ce a9 59  7c 93 4e 8c 9e bf 24 9e  |...h...Y|.N...$.|
00000130  e3 bc 40 24 54 3e c3 c0  7a 65 3e f4 6d d0 cc 69  |..@$T>..ze>.m..i|
00000140  46 e6 0a cd 89 ca 90 e7  8b 3f b8 da 42 57 d9 0b  |F........?..BW..|
00000150  c5 9f 66 05 f6 22 91 3c  b7 ad e5 f1 69 01 a4 14  |..f..".<....i...|
00000160  3b e7 96 88 9a 2f e1 35  5f 4c ca d3 e0 d4 62 4c  |;..../.5_L....bL|
00000170  0c bf ec 03 98 ce dc cc  9b 3a 5f 64 98 cf 33 2c  |.........:_d..3,|
00000180  10 80 05 1c d0 2f 00 fd  1c d0 27 34 a7 7d 4e f3  |...../....'4.}N.|
00000190  01 bc d4 e9 23 33 70 84  5d 87 b1 9f b1 ae 07 a9  |....#3p.].......|
000001a0  e1 f9 3d 68 3f 8d 19 64  3f 65 43 c3 66 78 51 45  |..=h?..d?eC.fxQE|
000001b0  6b cf a0 db 28 25 e5 a0  c7 d0 a6 0c e5 c0 00 3b  |k...(%.........;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 30 0c 11 00 00  |...........0....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on Popeye-root'


Unknown BootLoader on Popeye-swap_1'



=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/Popeye-root': No such file or directory
hexdump: /dev/mapper/Popeye-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/Popeye-swap_1': No such file or directory
hexdump: /dev/mapper/Popeye-swap_1': No such file or directory



```

---

### Post by bradburns on 2011-09-07
*BUMP*
Oh well. hmm.. forget about saving the server. What's the best way to pull an image off of ubuntu "server edition" (read: i dont want to use a GUI) 

:) Thanks in advance!

---

