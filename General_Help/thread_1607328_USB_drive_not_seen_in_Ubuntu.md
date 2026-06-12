---
title: "USB drive not seen in Ubuntu"
date: 2010-10-27
forum: General Help
---

### Post by rrc0406 on 2010-10-27
Hi,

I am fairly new to Ubuntu and was trying to read through the forums to seek help. I have never used a USB drive on my system. I was trying to configure it and went through nautilus and I see that it is already set to auto mount. I ran a few commands and this information might be helpful.

fdisk -l results into the following:
<
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060d66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ca44ca3
>

command blkid shows
<
/dev/sda1: UUID="5fc7042d-a631-4757-8264-5e13405cafee" TYPE="ext4" 
/dev/sda5: UUID="6ae7d51a-db7d-4f2d-93b7-45f8af7d7106" TYPE="swap" 
>

If anyone has any ideas with this issue I would appreciate some help.

---

### Post by efflandt on 2010-10-27
What kind of drive is it, and is it a drive purchased as a USB hard drive, or a regular internal or laptop drive in a USB enclosure?

Assuming the USB drive is sdb, a drive that size purchased as a USB drive would usually be formatted as FAT32 (vfat in Linux), unless formatted for a Mac.  But that drive does not appear to have any partition table or partitions on it at all (if new, or faulty if not new).

If the drive is new and unformatted, use Synaptic to install gparted, and then use System > Adminstration > Gparted to create an **msdos** partition table, and then whatever partitions you want on it.  You can have up to 4 primary or extended partitions, and an extended partition can contain any number of logical partitions.

FAT32 would be a most universally accessible file system for different devices and operating systems, but is limited to 4 GB maximum file size (not large enough for a DVD iso).

NTFS is most commonly used by WinXP or newer Windows OS.

Or you can use a Linux specific file system.

---

### Post by rrc0406 on 2010-10-27
This is a pen drive (1 GB). I do not see it when I execute fdisk command. However I do see it in the message log when I plug in the drive.

---

