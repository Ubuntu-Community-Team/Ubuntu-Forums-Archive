---
title: "How to automount USB drives as user?"
date: 2011-04-04
forum: General Help
---

### Post by Mr. Matt on 2011-04-04
My USB devices are being automounted as root in Ubuntu 10.10.  How can I automount them as the current user?

Here is the output of:

sudo fdisk -l
ls -l /dev/disk/by-uuid
df

For this example, /dev/sdc1 is connected.

```
matt@matt-G73Jw:/media$ sudo fdisk -l
[sudo] password for matt: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0c5913d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        2551       17750   122093748    7  HPFS/NTFS
/dev/sda3           17750       60802   345808896    f  W95 Ext'd (LBA)
/dev/sda5           17751       60802   345807872    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3040    24414062+  83  Linux
/dev/sdb2           30400       60801   244200992+   7  HPFS/NTFS
/dev/sdb3            3040       30400   219767809    5  Extended
/dev/sdb5            3040        4134     8788992   82  Linux swap / Solaris
/dev/sdb6            4134       30400   210977792   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 7958 MB, 7958691840 bytes
151 heads, 15 sectors/track, 6862 cylinders
Units = cylinders of 2265 * 512 = 1159680 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               4        6863     7768064    b  W95 FAT32
matt@matt-G73Jw:/media$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2011-04-04 20:43 24c93014-1a84-4fe4-942d-505d8d0c8052 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2011-04-04 20:43 2f39c808-de86-48dd-b79b-fa24777c95d2 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2011-04-04 20:43 3E5F-3A2B -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-04-04 20:43 60A4ED2DA4ED05FE -> ../../sdb2
lrwxrwxrwx 1 root root 10 2011-04-04 20:43 7f4e20f6-1bec-4a3f-b1e9-6770e951ba2d -> ../../sdb6
lrwxrwxrwx 1 root root 10 2011-04-04 20:43 827A05F07A05E1B1 -> ../../sda2
lrwxrwxrwx 1 root root 10 2011-04-04 20:43 8A07-A343 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2011-04-04 20:43 C636B1A236B193C1 -> ../../sda5
matt@matt-G73Jw:/media$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             24030952   4512252  18298000  20% /
none                   4049712       348   4049364   1% /dev
none                   4059352       924   4058428   1% /dev/shm
none                   4059352       108   4059244   1% /var/run
none                   4059352         0   4059352   0% /var/lock
/dev/sdb2            244200992 200391384  43809608  83% /media/SDATA2
/dev/sdb6            207666792  40267332 156850572  21% /home
/dev/sdc1              7763968   3827744   3936224  50% /media/usb0
/home/matt/.Private  207666792  40267332 156850572  21% /home/matt
/dev/sda5            345807868  66361944 279445924  20% /media/DATA
matt@matt-G73Jw:/media$ 

```

---

### Post by TeoBigusGeekus on 2011-04-04
Try
```
sudo chmod 777 /media/usb0
```
Do the same for all the mountpoints of your usb drives.

---

### Post by coffeecat on 2011-05-30
@Mr. Matt, I've only just come across this thread but I believe I have an answer. Your USB device is being mounted on /media/usb0 which suggests you are using the application usbmount. This should not be used on desktop systems as it interferes with the USB automounting functionality built into desktop versions of Ubuntu. I believe it is intended for GUI-less server systems. The fix is easy: uninstall it.

---

