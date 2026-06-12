---
title: "Can't see files on second hard drive"
date: 2009-08-07
forum: General Help
---

### Post by eadwacer on 2009-08-07
Recently bought new (500GB) HDD, installed Ubuntu/HH on it, and made it my primary (sda), with original (160GB) HDD as secondary (sdb). When I boot into new drive and mount HDD160, all I get is GRUB and Lost&Found (and some files).

fsck -l extract for sdb is:
----------------
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea3f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          30      234375   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              30       19458   156056528+   5  Extended
/dev/sdb5              30       19458   156056528   8e  Linux LVM
-----------------

As far as I can tell, mount will only work on sdb1. Trying to mount sdb or sdb2 gives error:

sshervais@ubuntu:/mnt/hdd160$ sudo mount -t ext3 /dev/sdb2 /mnt/hdd160
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,.....

So, when I get sdb1 mounted, here's what's in the directory:
sshervais@ubuntu:/mnt/hdd160$ ls
abi-2.6.20-16-generic             initrd.img-2.6.20-17-generic.bak
abi-2.6.20-17-generic             lost+found
config-2.6.20-16-generic          memtest86+.bin
config-2.6.20-17-generic          System.map-2.6.20-16-generic
grub                              System.map-2.6.20-17-generic
initrd.img-2.6.20-16-generic      vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak  vmlinuz-2.6.20-17-generic
initrd.img-2.6.20-17-generic

sdb1 is a separate bootable drive with Ubuntu/FF installed and all of my files on it. If I use it as the boot drive, it works, and everything is fine. I am sure I'm just missing a parameter, but I can't figure out what.

---

### Post by blueridgedog on 2009-08-07
sdb2 is an extended partition and can't be mounted.  sdb5 is the drive with all of your data, but it is part of a linux volume management set.  You can boot on the 160 gig drive and copy your data over to the larger drive or attempt to mount it.  Here is a good guide:

[http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html](http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html)

I have little experience with LVM, so I would probably boot on it and copy the data it it was my system, but others here may be able to help.  

You may get more people with LVM experience if you start a new thread of "how to mount an LVM volume"

---

### Post by eadwacer on 2009-08-08
BRD
Thanks, that's exactly what I needed. I booted the 160,  mounted the 500, copied files over and rebooted the 500. I suspect I'll be doing that a couple of more times, but my .Opera, .Evolution, and Documents files seem to have gotten most of it.

Thank you again
Steve Shervais

---

