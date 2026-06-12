---
title: "How to restore GRUB?"
date: 2010-06-29
forum: General Help
---

### Post by fasteddy342002 on 2010-06-29
Okay so i installed Mandriva today, but it got rid of my GRUB boot loader. So i need to know how to fix this, i have Ubuntu 10.04 installed, but am currently running the Live CD from 9.10 to get me online. So please will you help me people?

---

### Post by Rubi1200 on 2010-06-29
Hi,
you need to run the script from the link in my signature and then post the results back here. Someone can then hopefully help you resolve this problem.

Good luck!

---

### Post by fasteddy342002 on 2010-06-29
Here is the result:             




   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2010.0 
                       (Official) for i586 Kernel 2.6.31.5-desktop-1mnb on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb1710f3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63        80,324        80,262  de Dell Utility
/dev/sda2              80,325   135,684,989   135,604,665   7 HPFS/NTFS
/dev/sda4         135,684,990   488,392,064   352,707,075   5 Extended
/dev/sda5         135,685,053   160,874,909    25,189,857  83 Linux
/dev/sda6         240,798,348   478,238,984   237,440,637  83 Linux
/dev/sda7         478,239,048   488,392,064    10,153,017  82 Linux swap / Solaris
/dev/sda8         160,874,973   169,051,994     8,177,022  82 Linux swap / Solaris
/dev/sda9         169,052,058   240,798,284    71,746,227  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        7AEECA6D3BC74594                       ntfs       The Business                  
/dev/sda5        33793389-f82f-4974-8bc6-075a41ceac2d   ext4                                     
/dev/sda6        a94cfe9e-7ed4-4128-abe3-b2996ea4c461   ext4                                     
/dev/sda7        153c8271-8738-4fd4-8fa6-a102841b97d1   swap                                     
/dev/sda8        cbb497c8-6912-42e5-9e2d-77fc03dafd59   swap                                     
/dev/sda9        b3bc0a9e-a6d3-4f83-a5be-d278566cd720   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda6        /media/a94cfe9e-7ed4-4128-abe3-b2996ea4c461 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda9        /media/b3bc0a9e-a6d3-4f83-a5be-d278566cd720 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda2        /media/The Business      fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=33793389-f82f-4974-8bc6-075a41ceac2d  resume=UUID=153c8271-8738-4fd4-8fa6-a102841b97d1 splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=33793389-f82f-4974-8bc6-075a41ceac2d  resume=UUID=153c8271-8738-4fd4-8fa6-a102841b97d1
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=33793389-f82f-4974-8bc6-075a41ceac2d  failsafe
initrd (hd0,4)/boot/initrd.img

=============================== sda5/etc/fstab: ===============================

# Entry for /dev/sda5 :
UUID=33793389-f82f-4974-8bc6-075a41ceac2d / ext4 noatime 1 1
# Entry for /dev/sda9 :
UUID=b3bc0a9e-a6d3-4f83-a5be-d278566cd720 /home ext4 noatime 1 2
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sda2 :
UUID=7AEECA6D3BC74594 /media/windows ntfs-3g defaults,umask=000 0 0
none /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=153c8271-8738-4fd4-8fa6-a102841b97d1 swap swap defaults 0 0
# Entry for /dev/sda8 :
UUID=cbb497c8-6912-42e5-9e2d-77fc03dafd59 swap swap defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


  74.8GB: boot/grub/menu.lst
  74.8GB: boot/grub/stage2
  75.0GB: boot/initrd-2.6.31.5-desktop-1mnb.img
  75.0GB: boot/initrd-desktop.img
  75.0GB: boot/initrd.img
  71.9GB: boot/vmlinuz
  71.9GB: boot/vmlinuz-2.6.31.5-desktop-1mnb
  71.9GB: boot/vmlinuz-desktop

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a94cfe9e-7ed4-4128-abe3-b2996ea4c461
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a94cfe9e-7ed4-4128-abe3-b2996ea4c461
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a94cfe9e-7ed4-4128-abe3-b2996ea4c461
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a94cfe9e-7ed4-4128-abe3-b2996ea4c461 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a94cfe9e-7ed4-4128-abe3-b2996ea4c461
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a94cfe9e-7ed4-4128-abe3-b2996ea4c461 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a94cfe9e-7ed4-4128-abe3-b2996ea4c461
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a94cfe9e-7ed4-4128-abe3-b2996ea4c461
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a94cfe9e-7ed4-4128-abe3-b2996ea4c461 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=153c8271-8738-4fd4-8fa6-a102841b97d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 123.4GB: boot/grub/core.img
 135.3GB: boot/grub/grub.cfg
 128.5GB: boot/initrd.img-2.6.32-22-generic
 124.7GB: boot/vmlinuz-2.6.32-22-generic
 128.5GB: initrd.img
 124.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  51 30 de 26 52 13 27 68  2a 2d d0 4a 30 c1 c8 98  |Q0.&R.'h*-.J0...|
00000010  14 87 5b 9c 41 88 bb 3e  b3 82 67 bd 07 05 6b bd  |..[.A..>..g...k.|
00000020  ee 1b 5e cc 23 a4 6c a5  10 09 2e 58 cd e6 54 06  |..^.#.l....X..T.|
00000030  b5 27 63 87 31 0c 6f bd  97 f7 3d 1c 34 99 1b e9  |.'c.1.o...=.4...|
00000040  f1 f2 b1 33 00 cd 14 c1  c3 12 76 f2 11 2c 30 28  |...3......v..,0(|
00000050  ae 4c 2c c3 94 59 8d 5e  ad 1a 34 a7 99 61 f5 62  |.L,..Y.^..4..a.b|
00000060  2b a0 65 95 40 75 02 67  b1 49 7a d6 5c 47 fd 16  |+.e.@u.g.Iz.\G..|
00000070  e6 2c b2 47 12 2c 4c 15  f3 cc 6d 9f da ba 45 72  |.,.G.,L...m...Er|
00000080  d6 18 7e 90 3e 89 11 48  4f 54 81 30 6b cb 92 ae  |..~.>..HOT.0k...|
00000090  57 25 1f 49 54 a8 18 f1  47 99 e8 96 07 54 6e cf  |W%.IT...G....Tn.|
000000a0  6b db f3 49 d3 9f 08 f8  d3 6d 1f a2 4d ca 52 26  |k..I.....m..M.R&|
000000b0  1f 97 74 a6 4c 15 e6 0e  0a f1 6e 76 cf 0b ba 5f  |..t.L.....nv..._|
000000c0  04 b2 45 57 c8 cc 20 f6  9e 3f 30 f5 ed eb 0e a4  |..EW.. ..?0.....|
000000d0  45 b7 d6 63 cf ca ed 21  01 31 ef e4 db db 36 54  |E..c...!.1....6T|
000000e0  cf 63 87 6e ef ca 07 be  88 0a 3f f5 62 18 fa ca  |.c.n......?.b...|
000000f0  35 8b 46 0a 33 5c 50 f7  8f 53 e0 dd de 8f d4 b4  |5.F.3\P..S......|
00000100  b4 b6 93 ed 0f 2c cf b3  4f 8b 44 db 2c 9a b3 c4  |.....,..O.D.,...|
00000110  12 e8 69 8d e0 78 40 f9  6d 10 72 4a 9f 41 e1 3a  |..i..x@.m.rJ.A.:|
00000120  30 f7 26 08 98 5c 04 c3  d6 bd af 42 91 30 a3 c1  |0.&..\.....B.0..|
00000130  f7 da db 72 e6 6c 98 ac  08 1e 20 a7 5c 3d 7f 56  |...r.l.... .\=.V|
00000140  4a 53 c3 ea 40 2d 93 ec  2c e2 40 06 e8 fc 9c 70  |JS..@-..,.@....p|
00000150  f4 de 29 43 0d 15 56 88  a0 bf 85 ee f2 be a4 78  |..)C..V........x|
00000160  64 c9 5d 36 af 56 a0 52  b3 90 56 9d 34 55 a9 dd  |d.]6.V.R..V.4U..|
00000170  7f d0 eb 8c 62 eb 76 f5  df bb ea 48 f7 7a 44 e2  |....b.v....H.zD.|
00000180  86 af 0b 8a 0c d5 73 df  00 8f cb fb f3 39 86 8f  |......s......9..|
00000190  7b 92 76 e3 cd 35 17 c0  36 f7 8b 46 07 14 2c 05  |{.v..5..6..F..,.|
000001a0  79 61 21 eb 77 8a d0 7a  35 7a 1c 0e 47 a2 f7 63  |ya!.w..z5z..G..c|
000001b0  c0 8d cf c9 62 46 c3 f7  f9 1e 9d df f9 2f 00 fe  |....bF......./..|
000001c0  ff ff 83 fe ff ff 3f 00  00 00 e1 5d 80 01 00 fe  |......?....]....|
000001d0  ff ff 05 fe ff ff cf e6  43 06 bc 0e 27 0e 00 00  |........C...'...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by dino99 on 2010-06-29
you cant use grub1 (mandriva) with grub2 (lucid)

more info below

---

### Post by Rubi1200 on 2010-06-29
Thanks for the result. Please do us all a favor and edit the entry, highlight the text and then use the # tags; it makes things easier to read.

Ok, as far as your situation is concerned, Mandriva uses GRUB legacy (the older version) whereas Lucid uses GRUB2. When you installed Mandriva it overwrote Lucid's bootloader (as you know).

I believe the solution is to reinstall GRUB2, but I would rather wait for one of the core experts to come along and confirm this.

Hang in there!

---

### Post by wilee-nilee on 2010-06-29
What the above text says, and dino could you at the least point at the help link.;) In order to edit that txt you will have to hit edit then advanced to get to the panel with the # or use the instructions in my signature.

---

