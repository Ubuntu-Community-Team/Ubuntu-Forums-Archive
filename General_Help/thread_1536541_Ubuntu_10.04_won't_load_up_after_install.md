---
title: "Ubuntu 10.04 won't load up after install"
date: 2010-07-22
forum: General Help
---

### Post by sunseeker888 on 2010-07-22
Hi Guys

I just installed ubuntu on my pc, ubuntu 10.04.

Windows 7 was already installed on the system.

I wiped out sdd and did an install


Installation went ok.

I have 4 HDD


I installed Ubuntu on one of 1.5Gb HDD parition sdd.


When I rebooted, windows 7 started immediately. I have done a few installation before and this is the first time I have this problem.



Please see the steps I tried below, but still nothing after reboot, except the ugly win 7 boat.



Now I see there's a problem

first time it saw the linux partition on sdc

and see the second time it was on sdd


please see the different output





ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce939845

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 13 182402 1465033728 7 HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
240 heads, 63 sectors/track, 193801 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a9a2472

Device Boot Start End Blocks Id System
/dev/sdb1 1 193802 1465136128 7 HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc40b

Device Boot Start End Blocks Id System
/dev/sdc1 1 177907 1429030912 83 Linux
/dev/sdc2 177907 182402 36105217 5 Extended
/dev/sdc5 177907 182402 36105216 82 Linux swap / Solaris


I did the following and the output 

instruction from 
[https://help.ubuntu.com/community/Re...tallingWindows](https://help.ubuntu.com/community/Re...tallingWindows)


ubuntu@ubuntu:~$ mount | tail -1 
/dev/sdc1 on /media/72a8fe99-d0f3-46f5-9f49-5fa3a42e1266 type ext4 (rw,nosuid,nodev,uhelper=udisks)
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/72a8fe99-d0f3-46f5-9f49-5fa3a42e1266 /dev/sdc
Probing devices to guess BIOS drives. This may take a long time.
Installing GRUB to /dev/sdc as (hd2)...
Installation finished. No error reported.
This is the contents of the device map /media/72a8fe99-d0f3-46f5-9f49-5fa3a42e1266/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0) /dev/fd0
(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/sdc
ubuntu@ubuntu:~$


the above was what was expected, and after reboot, windows loaded up automatically again


2nd time 

~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ccbae3f

Device Boot Start End Blocks Id System
/dev/sda1 * 1 60802 488383488 7 HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce939845

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 13 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2 13 182402 1465033728 7 HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
240 heads, 63 sectors/track, 193801 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a9a2472

Device Boot Start End Blocks Id System
/dev/sdc1 1 193802 1465136128 7 HPFS/NTFS

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc40b

Device Boot Start End Blocks Id System
/dev/sdd1 1 177907 1429030912 83 Linux
/dev/sdd2 177907 182402 36105217 5 Extended
/dev/sdd5 177907 182402 36105216 82 Linux swap / Solaris
ubuntu@ubuntu:~$ mount | tail -1 
/dev/sdd1 on /media/72a8fe99-d0f3-46f5-9f49-5fa3a42e1266 type ext4 (rw,nosuid,nodev,uhelper=udisks)
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/72a8fe99-d0f3-46f5-9f49-5fa3a42e1266 /dev/sdd
Installation finished. No error reported.


now the above output was not what was expected, still no errors


but this was missing, and it did not probe the bios like before???



(fd0) /dev/fd0
(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/sdc
(hd3) /dev/sdd
ubuntu@ubuntu:~$


reboot still windows 7 load up


I followed this next instruction
[http://www.ubuntu-inside.me/2009/06/...r-windows.html](http://www.ubuntu-inside.me/2009/06/...r-windows.html)


$sudo mount /dev/sdd1 /mnt
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc

The following command is optional (it copies resolv.conf)

$sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

Now chroot into the enviroment we made :

sudo chroot /mnt

After chrooting, you do not need to add sudo before your commands because from now, you will run commands as root.

You may want to edit /etc/default/grub file to fit your system (timeout options etc)

#nano -w /etc/default/grub

Play with the options if you want.(But do not forget to give grub-update command if you saved it  )

Now install/recover Grub2 via :

#grub-install /dev/sda

command.However you may get errors with that code like me.If so please use this command :

#grub-install --recheck /dev/sda

Now you can exit the chroot, umount the system and reboot your box :

#exit
$sudo umount /mnt/dev
$sudo umount /mnt/proc
$sudo umount /mnt
$sudo reboot




Still windows load up


this is my grub.cfg

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
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 72a8fe99-d0f3-46f5-9f49-5fa3a42e1266
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
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 72a8fe99-d0f3-46f5-9f49-5fa3a42e1266
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 72a8fe99-d0f3-46f5-9f49-5fa3a42e1266
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=72a8fe99-d0f3-46f5-9f49-5fa3a42e1266 ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 72a8fe99-d0f3-46f5-9f49-5fa3a42e1266
echo 'Loading Linux 2.6.32-21-generic ...'
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=72a8fe99-d0f3-46f5-9f49-5fa3a42e1266 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 72a8fe99-d0f3-46f5-9f49-5fa3a42e1266
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 72a8fe99-d0f3-46f5-9f49-5fa3a42e1266
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
insmod ntfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ccdcba78dcba5c80
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
__________________
A banker is a fellow who lends you his umbrella when the sun is shining, but wants it back the minute it begins to rain.

---

### Post by sunseeker888 on 2010-07-22
Is the prob, the fact windows is on sdb instead sda? 


 sudo grub-install --root-directory=/media/72a8fe99-d0f3-46f5-9f49-5fa3a42e1266 /dev/sdb


reboot


I got the dreaded grub rescue


Panick. I started the system, inserted windows 7 disk to repair the mbr.

it repaired rebooted, weird the grub menu appear, and now I am in Ubuntu!!!!!!!!!!!!!!


but after rebooting again the grub appears.

---

