---
title: "Internal Hard Drive not booting, can't be mounted"
date: 2011-10-02
forum: General Help
---

### Post by Miqi on 2011-10-02
Before I had this problem, I was dual-booting 64-bit Vista and Ubuntu 11.04 with GRUB.
Now I can't access either partition on my hard drive, and my knoppix/ubuntu/fedora live usb can't access them either.

So here's how it happened:
I had been having some problems with vista (big surprise), for example windows was unable to load the installer for ANY new hardware , such as usb or virtual cdrom. I had a 64bit Windows 7 disk and decided to upgrade. Everything went smoothly, except for an error saying "windows could not load the installer for DiskDrive" that caused the installation to fail. The installer returned the os to normal, no problem. I did try one more time to upgrade, but got the same issue. So I gave up. The next time I turned on my laptop, Windows boot manager had replaced GRUB and only gave the option of booting Vista or windows setup for installing 7. I was still able to access the files in my ubuntu partition from live usb, so I backed up my user folder just in case. Later, a friend tried to fix the problem with EasyBCD in windows and wound up removing the option for vista as well. Now I can't boot into my ubuntu or Vista partition, and when I boot my live usb as I am doing now, file manager, disk utility, gparted and terminal can't access the hard drive.:confused:

This is a Dell Inspiron 1545 laptop from 2008, and I am live booting on a 16g usb 3.0 with YUMI.

So far from browsing the forums I've found that GParted can detect sda (the hard drive) but warns that it is an unrecognised disk label and shows it as 300 gigabytes of unallocated space.

This is what I get from sudo fdisk -l:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x280120b3

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1       29158   234205258    7  HPFS/NTFS
/dev/sda2           29158       38914    78363649    5  Extended
/dev/sda5           29158       38397    74210304   83  Linux
/dev/sda6           38397       38914     4152320   82  Linux swap / Solaris

Disk /dev/sdc: 15.8 GB, 15812526080 bytes
64 heads, 32 sectors/track, 15080 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     1574463     1785826   216435558+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?     1597667     2551505   976730017   16  Hidden FAT16
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?           1           1           0   6f  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4           24513      475848   462167897    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```As you can see, it displays the ntfs windows partition along with the ubuntu and linux swap partitions, but that is as far as I can get. I would really, really like to save my data and get my old computer back. Please help!!!

---

### Post by Miqi on 2011-10-02
P.S. I also created a boot-repair-disk live usb and ran the boot repair but that didn't do anything either.

---

### Post by Miqi on 2011-10-02
Another note: My friend did add an option for grub in the windows boot loader, and this takes me to the grub rescue prompt.

---

