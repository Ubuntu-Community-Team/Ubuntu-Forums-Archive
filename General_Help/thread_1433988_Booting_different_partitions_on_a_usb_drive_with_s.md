---
title: "Booting different partitions on a usb drive with syslinux"
date: 2010-03-19
forum: General Help
---

### Post by narnie on 2010-03-19
Hello,

I have an 8gb usb flash drive that I had high aspirations of using for a recovery/install/messing around multipurpose drive.

fdisk shows:

```
$ sudo fdisk -l /dev/sdb
[sudo] password for woodnt: 

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002815d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          65      522081    b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sdb2              66         977     7325640    5  Extended
/dev/sdb5             913         977      522081   82  Linux swap / Solaris
/dev/sdb6   *          66         161      771057    b  W95 FAT32
/dev/sdb7             162         249      706828+   b  W95 FAT32
```

I have used unetbootin to install a Linux mint LXDE liveCD iso which works great on sdb6

On sdb7, I have a regular Linux mint 64 bit liveCD iso.

It will boot into the LXDE environment no problem.

What I'm wanting to do is figure out how to "daisy-chain" the syslinux boot menu to the linux mint 64bit livecd's isolinux.cfg menu.

I see in syslinux, there is a syntax that will allow you to use a different .cfg file as so:

```
LABEL othermenu
	MENU LABEL Another Menu
	KERNEL menu.c32
	APPEND othermenu.conf

```

However, it will be on a different partition. I can't find a way to reference partitions from within syslinux .cfg syntax.

Can anyone help? Do I need to abandon syslinux and try something else? If so what?

Yours,
Narnie

below is the current syslinux.cfg file with an example of what I'm trying to do at the end (which I know won't work), but I need it to go to the filesystem on another partition:

```
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/mint.seed boot=casper quiet splash --

label ubnentry0
menu label Start Linux Mint LXDE
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper  quiet splash --

label ubnentry1
menu label Start Linux Mint LXDE (compatibility mode)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper xforcevesa  ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --

label ubnentry2
menu label Check the integrity of the CD
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry3
menu label Memory Test
kernel /isolinux/memtest
append initrd=/ubninit 

label ubnentry4
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit 

label ubnentry5
menu label Boot Linux Mint 64 bit
kernel /isolinux/vesamenu.c32
append isolinux/isolinux.cfg root=/dev/sdb7/
```

---

