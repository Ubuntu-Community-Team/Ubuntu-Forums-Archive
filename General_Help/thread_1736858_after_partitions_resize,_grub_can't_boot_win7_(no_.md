---
title: "after partitions resize, grub can't boot win7 (no such partition found)"
date: 2011-04-22
forum: General Help
---

### Post by finalni on 2011-04-22
I've resized partitions with some program - perhaps even gparted - but from Win7. partitions are indeed resized, but now I can't boot Win7, grub says
"no such device found"
"no such partition found"+01cbcrazyhexadecaddressmanwhichdoesntmeanmuch

I tried to use some advices on similar problems I found here (like adding GRUB_PRELOAD_MODULES="part_msdos"
to etc/default/grub and running grub-mkconfig after), but nothing helped.. I guess I could restore win7 with installation dvd but I want to fix GRUB (and have both ubuntu 10.10 and win7)

not sure if this could help you help me, but here is it:
```
john@john:~$ sudo fdisk -l
[sudo] password for john: 

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd576590b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         789     6336513    f  W95 Ext'd (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1476        4008    20346322+   7  HPFS/NTFS
/dev/sda3            4009        9964    47841570    7  HPFS/NTFS
/dev/sda5               1         749     6008832   83  Linux
/dev/sda6             749         789      326656   82  Linux swap / Solaris

```

---

### Post by Quackers on 2011-04-22
go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by finalni on 2011-04-23
here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046    12,675,071    12,673,026   f W95 Ext d (LBA)
/dev/sda5               2,048    12,019,711    12,017,664  83 Linux
/dev/sda6          12,021,760    12,675,071       653,312  82 Linux swap / Solaris
/dev/sda2    *     23,695,875    64,388,519    40,692,645   7 HPFS/NTFS
/dev/sda3          64,388,520   160,071,659    95,683,140   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,523,711 1,953,521,664   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        01CBF758144FD4F0                       ntfs                                     
/dev/sda3        01CBF756142B20D0                       ntfs       New Volume                    
/dev/sda5        72c4a373-4caf-48b9-af73-4d31bec6b4f7   ext4                                     
/dev/sda6        eecee743-4c15-4317-aae0-f096fd07eb0b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3E69-A33D                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/3E69-A33D         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_msdos
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
search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=72c4a373-4caf-48b9-af73-4d31bec6b4f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=72c4a373-4caf-48b9-af73-4d31bec6b4f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=72c4a373-4caf-48b9-af73-4d31bec6b4f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=72c4a373-4caf-48b9-af73-4d31bec6b4f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=72c4a373-4caf-48b9-af73-4d31bec6b4f7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=72c4a373-4caf-48b9-af73-4d31bec6b4f7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72c4a373-4caf-48b9-af73-4d31bec6b4f7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 01cbf758144fd4f0
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "FreeBSD" {
insmod ufs2
set root=(hd1,1)
chainloader +1
}

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
UUID=72c4a373-4caf-48b9-af73-4d31bec6b4f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=eecee743-4c15-4317-aae0-f096fd07eb0b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   2.5GB: boot/grub/core.img
   2.9GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-25-generic
   4.0GB: boot/initrd.img-2.6.35-27-generic
   6.0GB: boot/initrd.img-2.6.35-28-generic
   4.8GB: boot/vmlinuz-2.6.35-25-generic
   2.5GB: boot/vmlinuz-2.6.35-27-generic
   3.7GB: boot/vmlinuz-2.6.35-28-generic
   6.0GB: initrd.img
   4.0GB: initrd.img.old
   3.7GB: vmlinuz
   2.5GB: vmlinuz.old
```

---

### Post by TheHackOps on 2011-04-23
Have you tried "sudo apt-get update grub"
??

---

### Post by finalni on 2011-04-23
:redface:

I tried it now and it worked, thank you very much for your help :)

---

### Post by Quackers on 2011-04-23
All's well that ends well :-)
Please mark the thread as solved with the Thread Tools near the top of the page.

---

