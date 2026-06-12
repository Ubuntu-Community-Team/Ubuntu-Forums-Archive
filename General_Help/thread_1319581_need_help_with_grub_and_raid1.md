---
title: "need help with grub and raid1"
date: 2009-11-08
forum: General Help
---

### Post by ubdime on 2009-11-08
I installed 9.10 alternate to a degraded raid1. The plan was to add in a second hard drive in place of the cdrom and have it rebuild.

So it loads fine with 1 hard drive. In /boot/ are (abi,config,initrd.img,System.map,vmcoreinfo,vmlinuz)-2.6.31-14-generic files and the grub directory. In /boot/grub is a whole bunch of .mod files and device.map, which contains 2 lines (hd0) /dev/sda and (hd1) /dev/sdb

And just to be sure, I ran update-initramfs -u, then update-grub2.

So I should be ready to go, I shutdown, plug in 2nd hard drive. And I boot into the rescue prompt.

Grub loading.
error: file not found

grub rescue> ls
(md1) (hd0) (hd0,2) (hd0,1) (hd1) (hd1,2) (hd1,1)

grub rescue> set
prefix=(md1)/boot/grub
root=md1

grub rescue> ls /boot/grub
./ ../ device.map default installed-version (...) menu.lst (...)

Aha! So there's the problem. It's loaded md1, which is using my 2nd disk as the good disk.

grub rescue> set root=(hd0,1)

grub rescue> ls /boot/grub/
./ ../ (a whole bunch of .mod files including normal.mod)

grub rescue> insmod /boot/grub/normal.mod
error: file not found

Does anyone know why this doesn't work?

So the next step is unplug my master hd, boot with cdrom and slave so I can fdisk off the bad raid partition on the slave hd. And see if I can boot with mdadm selecting the correct disk. Unless you know a better way?

Any help is appreciated. Thanks.

---

