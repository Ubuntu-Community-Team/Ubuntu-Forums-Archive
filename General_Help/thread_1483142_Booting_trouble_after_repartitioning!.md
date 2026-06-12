---
title: "Booting trouble after repartitioning!"
date: 2010-05-14
forum: General Help
---

### Post by LeadHop on 2010-05-14
Hi - serious trouble here!

I had to resize my windows partition along with my ubuntu (lucid) partition to make more space on my windows partition.  Unfortunately, something went wrong, although unmentioned in gparted.  Now when i boot to linux, the splash screen pops up along with the message that there's something wrong with my power management.  

sometimes I can log in to a blank screen (alt f2 does nothing), sometimes i get stuck on a loop - log in, log in, log in.  I'd make this process easy just by backing everything up and reinstalling, but i have no more space on my external.  

What can I do from here? :confused:

---

### Post by wilee-nilee on 2010-05-14
> **LeadHop said:**
> Hi - serious trouble here!

I had to resize my windows partition along with my ubuntu (lucid) partition to make more space on my windows partition.  Unfortunately, something went wrong, although unmentioned in gparted.  Now when i boot to linux, the splash screen pops up along with the message that there's something wrong with my power management.  

sometimes I can log in to a blank screen (alt f2 does nothing), sometimes i get stuck on a loop - log in, log in, log in.  I'd make this process easy just by backing everything up and reinstalling, but i have no more space on my external.  

What can I do from here? :confused:

You should probably post this script, in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by LeadHop on 2010-05-14
thank you for the prompt reply!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11a8ba38

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2    *     10,233,405    51,167,024    40,933,620   7 HPFS/NTFS
/dev/sda3          51,167,025   312,576,704   261,409,680   5 Extended
/dev/sda5         306,600,588   312,576,704     5,976,117  82 Linux swap / Solaris
/dev/sda6          51,167,151   306,600,524   255,433,374  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2063 MB, 2063597568 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cff71

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4d1607f3-ee84-4a80-9256-023b2d4cff54   ext3                                     
/dev/sda1        0159-6699                              vfat       PQSERVICE                     
/dev/sda2        1ABC35FDBC35D3CB                       ntfs       ACER                          
/dev/sda5        64b388a0-4ca8-47e5-9ec0-013de26a4e47   swap                                     
/dev/sda6        5091dc59-8aef-4f44-b4c8-d0080bc56e4f   ext4                                     
/dev/sdb1        31BE-138A                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=5091dc59-8aef-4f44-b4c8-d0080bc56e4f ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=5091dc59-8aef-4f44-b4c8-d0080bc56e4f ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=5091dc59-8aef-4f44-b4c8-d0080bc56e4f ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=5091dc59-8aef-4f44-b4c8-d0080bc56e4f ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=5091dc59-8aef-4f44-b4c8-d0080bc56e4f ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=5091dc59-8aef-4f44-b4c8-d0080bc56e4f ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 5091dc59-8aef-4f44-b4c8-d0080bc56e4f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0159-6699
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1abc35fdbc35d3cb
	drivemap -s (hd0) ${root}
	chainloader +1
}
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
# / was on /dev/sda6 during installation
UUID=5091dc59-8aef-4f44-b4c8-d0080bc56e4f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=64b388a0-4ca8-47e5-9ec0-013de26a4e47 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  26.4GB: boot/grub/core.img
  29.5GB: boot/grub/grub.cfg
  41.4GB: boot/initrd.img-2.6.31-20-generic
  30.2GB: boot/initrd.img-2.6.32-21-generic
  34.1GB: boot/initrd.img-2.6.32-22-generic
  30.5GB: boot/vmlinuz-2.6.31-20-generic
  26.4GB: boot/vmlinuz-2.6.32-21-generic
  33.7GB: boot/vmlinuz-2.6.32-22-generic
  34.1GB: initrd.img
  30.2GB: initrd.img.old
  33.7GB: vmlinuz
  26.4GB: vmlinuz.old
```

i'd like to provide some help, but despite being a longtime user this is greek to me - thank you in advance for your assistance!

---

### Post by sedawk on 2010-05-14
Is Windows working (again)?
Have you done some file system checks with windows?

It is very strange that you see different problems every
time you boot Linux - I would expect that the error is
more repeatable.
Can you boot a LiveCD multiple times without any problems?
(You can try to run fsck (only scan, do not repair)
from the LiveCD to see if  any problems are reported on your disk).

Why is it you cannot reinstall Ubuntu?
Do you have any important data on the OS partitions
that are not part of the OS, e.g. have you
mounted /home on the root partition or stored important
data on the same partition?

In worst case you could try  to backup the important data
from Ubuntu (e.g. your /home) to the windows partition.
But actually I do not recommend that. If there really
is something wrong with your logical disk layout, there
might be more trouble to come.
I would backup to a (new) external disk as soon as possible without booting any of the OSes on the disk.
Then you can try to run file system checks that also
try to repair the disk.

---

### Post by LeadHop on 2010-05-14
The windows partition has no problems - i think the linux partition ran into a little trouble when shrinking and moving files during the repartitioning process.

Several more reboots later I'm now getting a consistent "splash screen, log in, log in, log in" intro, not that it's helping any, but that's what's going on.

I'm trying to avoid reinstalling ubuntu since i don't have any space on my external to backup my material on.  plus i'm thinking i wouldn't have a clue on how to get my old settings back without running into some form of trouble (mainly getting my internet settings back - extensions, saved tabs, etc. on firefox and chrome).  also, wouldn't transporting my /home folder into a new install of ubuntu just cause the same trouble again? :confused:

I tried running supergrub and booting linux from there but i got Error 15: file missing.  Not sure if that helps.

Also, running linux from my USB works fine as well.  I think the problem is mainly with the booting end on linux...

---

### Post by dino99 on 2010-05-14
why not simply remove/purge grub then install grub-pc and grub-common, when asked install grub2 on your ubuntu partition

---

### Post by LeadHop on 2010-05-14
> **dino99 said:**
> why not simply remove/purge grub then install grub-pc and grub-common, when asked install grub2 on your ubuntu partition

just to clear up, the problem isn't with the grub, but logging into linux.  I can't seem to get past the splash screen that asks for my password - and on the random occasion that it does, it shows a blank screen |-(.

but will reinstalling grub help?...  the grub works fine, it's the aftermath that's the problem.

---

### Post by LeadHop on 2010-05-14
ok - exciting new development!

I made a few phone calls and i'm able to borrow a friend's external.  so if i'm to copy the /home file, how do i set up my new setup to match my old one?  by that i mean having firefox, chrome, etc. to be set up as it was on my old install.  do i install chrome first then move in my /home file?  or does the order not matter?  file transfers are easy, but setting up extensions as it was on my old set up is not something familiar to me!

---

