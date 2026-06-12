---
title: "2 HDD's, Win 7/Ubuntu 10.10"
date: 2011-02-02
forum: General Help
---

### Post by drwackster on 2011-02-02
Hi,
Thanks for taking out the time to look at this...

I have windows 7 installed to one hard drive, and ubuntu 10.10 to another. however after installing, GRUB shows windows 7 in the list but when i pick it, it wont boot (just get a black screen with flashing cursor). F8 for windows boot menu doesnt even work.

Ubuntu will boot if i select ubuntu though. Do I need to fix the MBR using a windows disk? How does the boot loader work for Ubuntu? Does it overwrite the one windows has with GRUB?

Thanks! 
Steve


:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by YesWeCan on 2011-02-02
First, installing Ubuntu on a separate HD from Windows is a very good idea.
Second, completely disconnecting your Windows HD while installing Ubuntu is an even better idea.

If you have installed Ubuntu correctly, then your Windows HD will not have been changed at all. You can check this by selecting the boot menu in your bios and selecting to boot the Windows HD directly. If this does not work then you have modified the boot record on your Windows HD. Disconnect your Ubuntu HD for good measure and then boot off your Windows CD and repair your Windows boot.

Once you can boot directly into your Windows HD, disconnect it and reconnect the Ubuntu HD. Try to boot it. It may not boot and will require Grub to be re-installed. If so, boot a live CD and reinstall Grub. Then check you can boot off the Ubuntu HD.

Connect both HDs. Set the bios boot order to boot the Ubuntu HD first. Then reboot. You may not see a Grub menu this time. Once in Ubuntu, open a terminal and type 'sudo update-grub'. This will cause Grub to scan both your HDs and reconstruct its menu. Then  reboot. This time you should get a menu containing both Windows and Ubuntu. Select Windows and check it boots ok.

---

### Post by switch10 on 2011-02-02
Boot into Ubuntu, and post the output of:

```
sudo fdisk -l
```

This will list both HDD's, and the partitions on those disks.

---

### Post by drwackster on 2011-02-02
YesWeCan....Thanks so much for the constructed post. Its very accurate and once I get access to the right tools I can, Right now I am stuck in my college dorm so I will have to wait until the weekend. I really appreciate it though :)

Switch10: here you go:
320gb = windows 7
80gb=ubuntu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b3496e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15356928   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1912       38914   297211904    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060c1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9328    74920960   83  Linux
/dev/sdb2            9328        9730     3227649    5  Extended
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris

---

### Post by Quackers on 2011-02-02
From the Ubuntu desktop please tions > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by drwackster on 2011-02-02
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 12872736 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,715,903    30,713,856  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,715,904   625,139,711   594,423,808   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        C898AE5998AE45B2                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        cbc1e409-7b35-41cb-9db2-96fd05fe337f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set c898ae5998ae45b2
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=73c1e6d1-b959-4d86-80cf-3a9fcfb4fb53 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=cbc1e409-7b35-41cb-9db2-96fd05fe337f none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
   8.9GB: boot/grub/grub.cfg
    .3GB: boot/initrd.img-2.6.35-22-generic
   4.4GB: boot/vmlinuz-2.6.35-22-generic
    .3GB: initrd.img
   4.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  59 4f 18 26 5d 05 a0 55  d7 1e 3f 32 40 e1 8c 37  |YO.&]..U..?2@..7|
00000010  71 26 2c df 88 83 63 6f  47 e8 06 c3 5f 03 bb 6f  |q&,...coG..._..o|
00000020  82 71 3e d2 31 21 1b aa  c3 51 fb 99 31 dd 64 b6  |.q>.1!...Q..1.d.|
00000030  91 99 86 71 07 fb a3 f8  f1 75 12 08 2f 58 fb 67  |...q.....u../X.g|
00000040  d6 01 2e 29 6e cd 08 d2  6d d7 de 8b 18 3b 29 63  |...)n...m....;)c|
00000050  ca c8 de 48 67 f9 e2 f4  74 c4 11 f0 88 79 82 73  |...Hg...t....y.s|
00000060  f2 4a 92 64 fa 68 a1 c4  71 4d 93 e2 39 7d 5d 8f  |.J.d.h..qM..9}].|
00000070  96 02 4f db 99 70 35 b1  0b 57 2f 97 91 59 db 14  |..O..p5..W/..Y..|
00000080  d4 6c b8 e1 9a f2 f2 8d  f1 e9 11 7f ee 02 7e 38  |.l............~8|
00000090  3a b3 a8 fc 8c 99 3c 44  3f cb 0b cb 75 bc be 9e  |:.....<D?...u...|
000000a0  2f 26 eb 8b 60 95 71 86  48 aa 83 7c 79 66 5e f1  |/&..`.q.H..|yf^.|
000000b0  51 3e f4 07 97 cf bd f7  c1 49 df 98 37 bf 20 08  |Q>.......I..7. .|
000000c0  4b 66 3f 6a 6e 38 51 df  38 8f 7c d6 6b 33 40 87  |Kf?jn8Q.8.|.k3@.|
000000d0  75 af 1f 59 d6 2e 5c dc  0c a7 c5 ff 7f 09 1d 0a  |u..Y..\.........|
000000e0  6a 39 b5 97 b4 3e f6 35  6c df 9f 30 0f f8 8e 8c  |j9...>.5l..0....|
000000f0  90 51 dc e8 a4 04 86 b6  4e 73 d6 b6 db 47 73 77  |.Q......Ns...Gsw|
00000100  86 34 ed ad 82 3c 2c 39  45 c6 73 2f ff 16 58 17  |.4...<,9E.s/..X.|
00000110  82 45 2a d8 65 c5 de 55  cf 95 ad b1 ea 43 db 48  |.E*.e..U.....C.H|
00000120  ae 8d 2f b3 69 85 01 d0  b8 28 99 10 63 3e 49 d9  |../.i....(..c>I.|
00000130  a0 4f df 16 5c 9f 1c 75  f5 7a 19 7b 89 d0 19 23  |.O..\..u.z.{...#|
00000140  8c f6 b3 d4 c4 5a 86 61  42 a5 24 ce 70 00 f7 75  |.....Z.aB.$.p..u|
00000150  e6 83 0a 82 92 5d 13 ea  ac 5b 68 50 d0 c7 a8 75  |.....]...[hP...u|
00000160  a3 d9 a8 66 13 6d 7b 12  7c 40 2f df a1 df cf 34  |...f.m{.|@/....4|
00000170  d5 2c 48 56 9e a0 2e 94  dc fb bc ae cd 2d 27 ad  |.,HV.........-'.|
00000180  4d 8d 8f dd 78 21 28 19  64 b5 26 04 f3 65 06 4c  |M...x!(.d.&..e.L|
00000190  48 79 85 ff 13 a3 3f 15  e1 e7 b7 4a b4 74 e3 59  |Hy....?....J.t.Y|
000001a0  05 d1 a5 95 8f 8f cf d4  8e 81 f5 95 f8 30 5e 77  |.............0^w|
000001b0  85 bf 66 62 d3 a9 ae 15  8d 90 e9 19 a6 53 00 fe  |..fb.........S..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Thank you!!! I appreciate the extra mile

---

### Post by Quackers on 2011-02-02
It appears that at some time you have installed grub to /dev/sda2. This is your Windows 7 partition and it won't like that :-)
I would suggest that you make your Windows drive the first bootable hard drive in your bios (if it isn't already) and then run the startup repair (up to 3 times) from the recovery environment of the Windows repair disc or installation disc (not a recovery dvd). If Windows then boots ok you can then make the Ubuntu drive the first bootable hard drive in the bios, then re-install grub to that drive from the live cd/usb.

---

### Post by drwackster on 2011-02-02
Wow, thanks a LOT..I appreciate it! Can I send cookies or something-lol.
I hope i can be in your place one day and be able to answer questions like this. Thanks again especially to everyone else who answered!!!


:popcorn:

---

