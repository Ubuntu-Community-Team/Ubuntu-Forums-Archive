---
title: "can't boot to ubuntu and windows"
date: 2011-05-05
forum: General Help
---

### Post by ][soSo][ on 2011-05-05
hi everyone
i'm beginner... i have ubuntu10.10 and windows XP on my laptop

i installed Burg manager to change boot theme
and i think i did wrong installation

now when i turn my laptop on i get black screen and there is no boot for windows or ubunto

this is what i get

[http://i53.tinypic.com/2evw0td.jpg](http://i53.tinypic.com/2evw0td.jpg)

how i can fix this problem!! 
i'm not ready to format and lose my files on booth OS.

---

### Post by karthick87 on 2011-05-05
Pls run the bootinfoscript from my signature. And post the results with code(#) tag, so that it will be easy for us to help you :)

---

### Post by anderson.fonseca on 2011-05-05
Start your laptop with Ubuntu livecd and try to install the grub again.

---

### Post by Rubi1200 on 2011-05-05
> **anderson.fonseca said:**
> Start your laptop with Ubuntu livecd and try to install the grub again.
Which wouldn't be very sensible if the OP has a Wubi install as it will only complicate matters.

@][soSo][; follow the advice posted by karthick87.

---

### Post by anderson.fonseca on 2011-05-05
I got it Rubi1200, because Wubi run alongside with Windows system. In this case, that's true.

---

### Post by ][soSo][ on 2011-05-05
thanks you all for helping me  =) 


ok now i run LiveCD and installed the script and this is the result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,297,024    83,296,962   7 HPFS/NTFS
/dev/sda2          83,297,086   114,206,084    30,908,999   f W95 Ext d (LBA)
/dev/sda5          83,297,088   114,206,084    30,908,997   7 HPFS/NTFS
/dev/sda3         114,206,720   154,343,423    40,136,704  83 Linux
/dev/sda4         154,343,424   156,301,311     1,957,888  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        C874A88A74A87CB6                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        4abf0529-d30b-4e21-9de0-fc401261aad0   ext4                                     
/dev/sda4        f68eaf96-4066-4bea-a90b-bfea36ebe4f2   swap                                     
/dev/sda5        FA8471FB8471BAA9                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/4abf0529-d30b-4e21-9de0-fc401261aad0 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 4abf0529-d30b-4e21-9de0-fc401261aad0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 4abf0529-d30b-4e21-9de0-fc401261aad0
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4abf0529-d30b-4e21-9de0-fc401261aad0
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=4abf0529-d30b-4e21-9de0-fc401261aad0 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4abf0529-d30b-4e21-9de0-fc401261aad0
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=4abf0529-d30b-4e21-9de0-fc401261aad0 ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4abf0529-d30b-4e21-9de0-fc401261aad0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4abf0529-d30b-4e21-9de0-fc401261aad0 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4abf0529-d30b-4e21-9de0-fc401261aad0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4abf0529-d30b-4e21-9de0-fc401261aad0 ro single  splash
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4abf0529-d30b-4e21-9de0-fc401261aad0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 4abf0529-d30b-4e21-9de0-fc401261aad0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c874a88a74a87cb6
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=f68eaf96-4066-4bea-a90b-bfea36ebe4f2 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  71.7GB: boot/grub/core.img
  61.0GB: boot/grub/grub.cfg
  59.7GB: boot/initrd.img-2.6.35-22-generic
  59.7GB: boot/initrd.img-2.6.35-28-generic
  71.7GB: boot/vmlinuz-2.6.35-22-generic
  71.8GB: boot/vmlinuz-2.6.35-28-generic
  59.7GB: initrd.img
  59.7GB: initrd.img.old
  71.8GB: vmlinuz
  71.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  36 db f8 db 6f e3 6d bf  8d b6 fe 36 db f8 db 6f  |6...o.m....6...o|
00000010  e3 6d bf 8d b6 fe 36 db  f8 db 6f e3 6d bf 8d b6  |.m....6...o.m...|
00000020  fe 36 db f8 db 6f e3 6d  bf 8d b6 fe 36 db f8 db  |.6...o.m....6...|
00000030  6f e3 6d bf 8d b6 fe 36  db f8 db 6f e3 6d bf 8d  |o.m....6...o.m..|
00000040  b6 fe 36 db f8 db 6f e3  6d bf 8d b6 fe 36 db f8  |..6...o.m....6..|
00000050  db 6f e3 6d bf 8d b6 fe  36 db f8 db 6f e3 6d bf  |.o.m....6...o.m.|
00000060  8d b6 fe 36 db f8 db 6f  e3 6d bf 8d b6 fe 36 db  |...6...o.m....6.|
00000070  f8 db 6f e3 6d bf 8d b6  fe 36 db f8 db 6f e3 6d  |..o.m....6...o.m|
00000080  bf 8d b6 fe 36 db f8 db  6f e3 6d bf 8d b6 fe 36  |....6...o.m....6|
00000090  db f8 db 6f e3 6d bf 8d  b6 fe 36 db f8 db 6f e3  |...o.m....6...o.|
000000a0  6d bf 8d b6 fe 36 db f8  db 6f e3 6d bf 8d b6 fe  |m....6...o.m....|
000000b0  36 db f8 db 6f e3 6d bf  8d b6 fe 36 db f8 db 6f  |6...o.m....6...o|
000000c0  e3 6d bf 8d b6 fe 36 db  f8 db 6f e3 6d bf 8d b6  |.m....6...o.m...|
000000d0  fe 36 db f8 db 6f e3 6d  bf 8d b6 fe 36 db f8 db  |.6...o.m....6...|
000000e0  6f e3 6d bf 8d b6 fe 36  db f8 db 6f e3 6d bf 8d  |o.m....6...o.m..|
000000f0  b6 fe 36 db f8 db 6f e3  6d bf 8d b6 fe 36 db f8  |..6...o.m....6..|
00000100  db 6f e3 6d bf 8d b6 fe  36 db f8 db 6f e3 6d bf  |.o.m....6...o.m.|
00000110  8d b6 fe 36 db f8 db 6f  e3 6d bf 8d b6 fe 36 db  |...6...o.m....6.|
00000120  f8 db 6f e3 6d bf 8d b6  fe 36 db f8 db 6f e3 6d  |..o.m....6...o.m|
00000130  bf 8d b6 fe 36 db f8 db  6f e3 6d bf 8d b6 fe 36  |....6...o.m....6|
00000140  db f8 db 6f e3 6d bf 8d  b6 fe 36 db f8 db 6f e3  |...o.m....6...o.|
00000150  6d bf 8d b6 fe 36 db f8  db 6f e3 6d bf 8d b6 fe  |m....6...o.m....|
00000160  36 db f8 db 6f e3 6d bf  8d b6 fe 36 db f8 db 6f  |6...o.m....6...o|
00000170  e3 6d bf 8d b6 fe 36 db  f8 db 6f e3 6d bf 8d b6  |.m....6...o.m...|
00000180  fe 36 db f8 db 6f e3 6d  bf 8d b6 fe 36 db f8 db  |.6...o.m....6...|
00000190  6f e3 6d bf 8d b6 fe 36  db f8 db 6f e3 6d bf 8d  |o.m....6...o.m..|
000001a0  b6 fe 36 db f8 db 6f e3  6d bf 8d b6 fe 36 db f8  |..6...o.m....6..|
000001b0  db 6f e3 6d bf 8d b6 fe  36 db f8 db 6f e3 00 01  |.o.m....6...o...|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 45 a2 d7 01 00 00  |..........E.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

i hope this is good informations for you to help me solving this problem.   =)

---

### Post by ][soSo][ on 2011-05-05
any idea ?

---

### Post by Rubi1200 on 2011-05-05
I've never used a boot manager like burg so I actually have little idea of what it might have done to mess up the MBR or anything else.

However, this is what you should at least try as a first step to fix this from a LiveCD:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda3 /mnt

sudo grub-install --root-directory=/mnt /dev/sda
```

Once finished, reboot taking out the CD. Once you are back in Ubuntu run this command to pick up the Windows install:

```
sudo update-grub
```

Let me know what happens.

---

### Post by ][soSo][ on 2011-05-05
@Rubi1200 
thank you very very much

that's helped me to restore boot menu
now i'm back to my lovely Ubuntu OS  =D  (L)
....
ok now i'm wondering how i can change boot theme, hope not with "burg manager" because it's never work fine with me.. every time i choose a theme it won't change.

maybe i have wrong way installed that!!
what is your advice plz  =)

---

### Post by Rubi1200 on 2011-05-05
First of all, I am really pleased you can boot again :-)

About changing the boot theme, I don't know. I never play around with stuff like that. But it you do a search on the forums I am sure you will find some information.

Please mark this thread Solved using the Thread Tools near the top of the page if you think the problem is resolved now.

By the way, is Windows also booting normally?

---

### Post by ][soSo][ on 2011-05-05
ok i will search to find another way to change boot theme.

the problem is solved and the boot menu is back,
booth Ubuntu and Windows is booting fine now without any problems.

thank you all for help =)

---

