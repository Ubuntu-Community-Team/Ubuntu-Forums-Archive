---
title: "help with install grub in external hard driver"
date: 2011-03-19
forum: General Help
---

### Post by Meantsaki on 2011-03-19
i am new,i am trying 4 days now in the forum but i cant find anything that could help me...i have ask somebody and told me to download grub to mbr to external drive i find some sudo commands but i found some errors like no mount...i dont understant...please give some more details

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: __________________________________________________  _______________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________  _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb6: __________________________________________________  _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________  ___

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


Drive: sdb ___________________ __________________________________________________  ___

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,881,580,711 1,881,580,649   7 HPFS/NTFS
/dev/sdb2       1,881,581,566 1,953,523,711    71,942,146   5 Extended
/dev/sdb5       1,881,581,568 1,950,474,239    68,892,672  83 Linux
/dev/sdb6       1,950,476,288 1,953,523,711     3,047,424  82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________  __________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A6C6C425C6C3F419                       ntfs       System Reserved               
/dev/sda2        7AC4C671C4C62F67                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5ED0D8E3D0D8C307                       ntfs       FreeAgent Drive               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        519fc60e-3b13-49e6-985f-2f8fb29c8fad   ext4                                     
/dev/sdb6        65314d5b-cc94-49d2-b92e-7d6105603548   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/7AC4C671C4C62F67  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_  permissions)
/dev/sdb1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_  permissions)
/dev/sdb5        /media/519fc60e-3b13-49e6-985f-2f8fb29c8fad ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(:cool:, info grub, update-grub(:cool:
#            grub-install(:cool:, grub-floppy(:cool:,
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=519fc60e-3b13-49e6-985f-2f8fb29c8fad

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-27-generic
uuid        519fc60e-3b13-49e6-985f-2f8fb29c8fad
kernel        /boot/vmlinuz-2.6.35-27-generic root=UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad ro quiet splash 
initrd        /boot/initrd.img-2.6.35-27-generic

title        Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid        519fc60e-3b13-49e6-985f-2f8fb29c8fad
kernel        /boot/vmlinuz-2.6.35-27-generic root=UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad ro  single
initrd        /boot/initrd.img-2.6.35-27-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        519fc60e-3b13-49e6-985f-2f8fb29c8fad
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        519fc60e-3b13-49e6-985f-2f8fb29c8fad
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        519fc60e-3b13-49e6-985f-2f8fb29c8fad
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        519fc60e-3b13-49e6-985f-2f8fb29c8fad
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 519fc60e-3b13-49e6-985f-2f8fb29c8fad
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 519fc60e-3b13-49e6-985f-2f8fb29c8fad
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 519fc60e-3b13-49e6-985f-2f8fb29c8fad
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 519fc60e-3b13-49e6-985f-2f8fb29c8fad
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 519fc60e-3b13-49e6-985f-2f8fb29c8fad
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 519fc60e-3b13-49e6-985f-2f8fb29c8fad
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 519fc60e-3b13-49e6-985f-2f8fb29c8fad
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 519fc60e-3b13-49e6-985f-2f8fb29c8fad
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a6c6c425c6c3f419
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=519fc60e-3b13-49e6-985f-2f8fb29c8fad /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=65314d5b-cc94-49d2-b92e-7d6105603548 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 989.2GB: boot/grub/core.img
 978.5GB: boot/grub/grub.cfg
 989.2GB: boot/grub/menu.lst
 989.3GB: boot/grub/stage2
 964.2GB: boot/initrd.img-2.6.35-22-generic
 987.2GB: boot/initrd.img-2.6.35-27-generic
 989.2GB: boot/vmlinuz-2.6.35-22-generic
 989.3GB: boot/vmlinuz-2.6.35-27-generic
 987.2GB: initrd.img
 964.2GB: initrd.img.old
 989.3GB: vmlinuz
 989.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  90 3c aa 68 15 6f eb 98  c5 71 12 10 77 68 31 dd  |.<.h.o...q..wh1.|
00000010  b5 94 f5 ae 63 61 c8 07  71 71 d9 1f 17 18 1b 75  |....ca..qq.....u|
00000020  f6 b1 28 b4 05 ed 3b 03  82 51 8b 7d f2 f8 49 b1  |..(...;..Q.}..I.|
00000030  0a 23 3a dc f1 c1 1f 76  b1 04 96 cd 79 bf 2c ab  |.#:....v....y.,.|
00000040  1d b6 89 cf 1d 5c 48 64  bc 75 4f 45 ff 47 a8 bc  |.....\Hd.uOE.G..|
00000050  db fe b0 14 74 20 11 91  0f 55 43 9c 55 dc a4 4d  |....t ...UC.U..M|
00000060  03 8d f6 05 06 bc db 6e  5f 77 74 08 ef 5b 68 2f  |.......n_wt..[h/|
00000070  37 a7 29 1f c4 37 5e 42  ca 07 0b 42 0c 2e 03 c7  |7.)..7^B...B....|
00000080  7d 92 bd ea 62 6d 3c 06  d7 27 ff d8 fb 8c f2 fe  |}...bm<..'......|
00000090  ae c3 8d af bd 59 b4 8a  ce ce 38 3e 13 ec 2e 80  |.....Y....8>....|
000000a0  4a 11 3b 1e f5 18 2b af  89 c0 c9 bf 65 21 40 97  |J.;...+.....e!@.|
000000b0  49 0e 0b 15 52 09 2c 15  68 7c b0 a4 8c 97 1d 7b  |I...R.,.h|.....{|
000000c0  15 0b 63 f2 1e c0 74 75  45 62 83 3d 08 a0 93 5a  |..c...tuEb.=...Z|
000000d0  7a 7d 1d f2 54 bf 5b 13  3e aa a0 10 a3 1e 8f 06  |z}..T.[.>.......|
000000e0  bc 11 5b 86 30 a2 fa 40  e8 e2 af ba c7 a2 7e bc  |..[.0..@......~.|
000000f0  70 10 70 c3 04 bc a5 4f  ac 01 fd 43 1b 4c 41 c4  |p.p....O...C.LA.|
00000100  09 d3 72 7a 57 5d f2 4a  27 08 a7 8b 69 73 6a d6  |..rzW].J'...isj.|
00000110  18 f6 02 fa 46 11 a1 7b  5d 5c 3c a1 d4 8b 57 27  |....F..{]\<...W'|
00000120  e7 97 ee a4 7e 6b fa fc  8b 78 65 a8 a5 24 5f 0f  |....~k...xe..$_.|
00000130  51 a6 54 ed dc 77 26 93  32 8c 59 c6 42 eb b6 16  |Q.T..w&.2.Y.B...|
00000140  de 8e 0f 4d 54 98 e7 2a  e4 df be ea cd f5 de 95  |...MT..*........|
00000150  ad ad 6d b4 2f a4 4f cd  1d 7d ee 9c 86 67 14 c9  |..m./.O..}...g..|
00000160  64 f7 9f 99 7e 8e 22 cd  9b f0 d5 c8 3d 81 76 d6  |d...~.".....=.v.|
00000170  67 24 fa aa 45 fa 10 3b  3e 26 3c 67 eb cb 3c 9f  |g$..E..;>&<g..<.|
00000180  5b a5 31 fd e8 2b 0c 48  8c 39 92 16 22 e8 4d 1a  |[.1..+.H.9..".M.|
00000190  24 50 03 d6 2b 17 68 9f  3d a1 cf c7 56 64 db ac  |$P..+.h.=...Vd..|
000001a0  a6 86 26 a0 ac 1d b5 31  d8 8d 9c 5b 8c 8c c8 bb  |..&....1...[....|
000001b0  b3 a4 74 43 4c b8 6b 97  6f 0e 65 f2 af 91 00 fe  |..tCL.k.o.e.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 38 1b 04 00 fe  |...........8....|
000001d0  ff ff 05 fe ff ff 02 38  1b 04 00 88 2e 00 00 00  |.......8........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by wilee-nilee on 2011-03-19
sdb5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.10
Boot files/dirs: **/boot/grub/menu.lst** /boot/grub/grub.cfg /etc/fstab
/boot/grub/core.img

You have grub-legacy highlighted and grub2 you can't use both.

If you can boot to the Ubuntu follow the non chroot method in this link, ask any questions needed. Your going to purge all things grub then install grub2 back.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I would go with grub2 if it were  me it will auto find other OS's. When you r finished make sure the sdb drive is first in the bios to be read first. We are assuming to that the bios is set to read half way or so into the HD.

---

### Post by garvinrick4 on 2011-03-19
+1 with purge both grub, grub-pc and grub-common and reinstall grub-pc and grub-common into sdb with wilee-nilee.

---

### Post by Meantsaki on 2011-03-19
thanks for the quick replay but i am new to all these and they seems to me greek.I can boot only with Live CD...what i do next...i read the link but has so many cases(and i am no good in english) that i cant findwhat to do first...and i wna t to ask something...when we fix the problem, i must have the extrernal plug in in order to boot from internal HDD...thank again 

ps i have seperate boot partition?

---

### Post by garvinrick4 on 2011-03-19
Put Live Cd get internet connection and Copy and Paste these one at a time.
```
sudo mount /dev/sdb5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
apt-get update
``` ```
apt-get purge grub grub-common grub-pc
``````
install grub-common grub-pc
``````
update-grub
``````
exit
```                           ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
``````
sudo shutdown -h now
```Start machine and boot into either windows or Ubuntu when USB drive plugged in.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
This link wilee-nilee gave you explains the commands:
Live CD with chroot and internet connection.

---

### Post by Meantsaki on 2011-03-19
mount: special device /dev/sdb5 does not exist
 it appierce this error with the first command...all day i am against this error...thank again

ps.agian the same error...

---

### Post by garvinrick4 on 2011-03-19
Run this and see if it is still there:
```
sudo fdisk -l
``` (lower case L)

---

### Post by Meantsaki on 2011-03-19
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A6C6C425C6C3F419                       ntfs       System Reserved               
/dev/sda2        7AC4C671C4C62F67                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/7AC4C671C4C62F67  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```my last bootinfo...i have always this moun error
i wnat to kill myself...i am too tired, i am sorry i plugged of...i tried again...i am very sorry

---

### Post by garvinrick4 on 2011-03-19
There is no sdb in the last boot script, do you have it plugged into a USB?

For sda use this
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
only a couple of commands and real simple.
sda is internal drive
sdb is external drive
internal has Windows
external has Linux

---

### Post by Meantsaki on 2011-03-20
sorry for yerterday, i was so tired that at the end i  lost it...now with clear head seams so easier...all worked until i did  command:apt-get purge grub grub-common grub-pc 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
Package grub-common is not installed, so not removed
Package grub-pc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
```

the next command doesnt work...here is fdisk after mount

```
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0dda5797

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb27154e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      117123   940790324+   7  HPFS/NTFS
/dev/sdb2          117124      121602    35971073    5  Extended
/dev/sdb5          117124      121412    34446336   83  Linux
/dev/sdb6          121412      121602     1523712   82  Linux swap / Solaris

```

---

### Post by garvinrick4 on 2011-03-20
*You now have no grub installed in sdb (usb drive) so install grub-pc and grub-common: instructions below
#Put in Live cd and get an Internet connection(need the internet connection)
                     ```
sudo mount /dev/sdb5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

 
``````
apt-get update
``````
apt-get install grub-pc grub-common
``````
update-grub
``````
exit
```                    ```

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
``````
sudo shutdown -r now
```

---

