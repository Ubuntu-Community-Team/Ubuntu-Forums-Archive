---
title: "Sandisk pendrive shows unexpected behaviour"
date: 2012-02-05
forum: General Help
---

### Post by Vishnu V on 2012-02-05
Hi 
When i insert a sandisk pendrive into ubuntu 11.10, 2 devices are showing in nautilus,3 drives are in disk utility. Only one can mount and when i tried to mount the normail drive (icon of usb) it gives the error even before mounting the other drive
```

Error mounting: mount: /dev/sdc1 already mounted or /media/9889-D3B5 busy

```
output of fdisk -l 
```

vishnu@vishnu-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    99997695    49997824   83  Linux
/dev/sda2        99999744   112005179     6002718   82  Linux swap / Solaris
/dev/sda3   *   112007168   164423679    26208256    7  HPFS/NTFS/exFAT
/dev/sda4       164425399   625121279   230347940+   5  Extended
/dev/sda5       216861498   625121279   204129891   83  Linux
/dev/sda6       164425464   216861434    26217985+  83  Linux












Partition table entries are not in disk order

Disk /dev/mapper/1SanDisk: 8004 MB, 8004304896 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000672f1

               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/1SanDisk1   *          62    15620279     7810109    c  W95 FAT32 (LBA)

Disk /dev/mapper/1SanDisk-part1: 7997 MB, 7997551616 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15620218 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb0eb409

This doesn't look like a partition table
Probably you selected the wrong device.

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/1SanDisk-part1p1   ?  3447419926  5314066216   933323145+  66  Unknown
/dev/mapper/1SanDisk-part1p2   ?        2573        2573           0   72  Unknown

Partition table entries are not in disk order

Disk /dev/sdc: 8004 MB, 8004304896 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000672f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15620279     7810109    c  W95 FAT32 (LBA)


```


output of df
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             49212224  32160204  14552132  69% /
udev                   1531036         4   1531032   1% /dev
tmpfs                   617196      1100    616096   1% /run
none                      5120         0      5120   0% /run/lock
none                   1542984       448   1542536   1% /run/shm
/dev/mapper/1SanDisk-part1
                       7794860    854324   6940536  11% /media/9889-D3B5


```


What my problem is that i cann't install ubuntu into the usb using usb disk creator.It dont detect my usb 

Attaching screenshot of disk utility ,and nautilus. In disk utilty
2 8GB hard disk and Sandisk all coresponds to same pendrive

Sorry for my bad English

Thanks 
Vishnu V

---

### Post by jwbrase on 2012-02-05
I have a pair of SanDisk USB sticks as well, and as I recall they came with some odd partitioning scheme set up to support some windows-only software they had pre-installed that was supposed to provide some extra functionality. Ubuntu is mounting each partition on the drive, which is why you're seeing more than one drive.

The extra software also interferes with the USB disk creator, see [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Just remove it and repartition the drive and it should behave normally.

---

### Post by Vishnu V on 2012-02-05
Thanks for the reply, repartitioning not solved my problem
Ubuntu 10.10 and 12.04 has no such problems

---

### Post by Vishnu V on 2012-02-17
Ok. I got solution for the problem, but it is temporary
Sokution is
```

sudo dmsetup remove_all

```
code will remove all unwanted partitions listing from disk utilty,nautilus etc.
I can mount the drive as usual, Startup disk creator also detects the drive

I have to do all the i insert the pendrive



Any Solution ?

Thank you
Vishnu V

---

### Post by Dlambert on 2012-02-17
If the pendrive is brand new, most companies partitions it for use with their software. Just Set up a new MBR and format a partition. Hope this helps!

Open up disk utility

Find the drive

Unmount all partitions

Then hit "format volume" Select MBR

Then select the partition and format it to Ext4 (Linux only) or Fat (Universal DEFAULT) or whatever format you wish

Then let it finish and remount. Enjoy

---

### Post by Dlambert on 2012-02-17
> **jwbrase said:**
> I have a pair of SanDisk USB sticks as well, and as I recall they came with some odd partitioning scheme set up to support some windows-only software they had pre-installed that was supposed to provide some extra functionality. Ubuntu is mounting each partition on the drive, which is why you're seeing more than one drive.

The extra software also interferes with the USB disk creator, see [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Just remove it and repartition the drive and it should behave normally.

+1 Again, just format the drive using disk utility. I think the key is the MBR ^^^

---

### Post by Vishnu V on 2012-02-17
Thanks for the reply, but it not solved my problem
Pendrive is new, but  Ubuntu 12.04 & 10.10, have no such problem,

And one more thing i cant evevn format the drive from disk utility (ubuntu 11.10)
When i tried to create Ext4  partition it says
```

Error Creating partition
One or more block devices are holding /dev/sdb

```

I format it from ubuntu 12.04 but still problem is there

---

### Post by Dlambert on 2012-02-17
Try in windows

---

### Post by Vishnu V on 2012-02-17
Sorry, that dont works
Still problem is there

---

### Post by abdulwadhood on 2012-05-25
Have the same problem with my SanDisk Cruzer 16GB on Toshiba Satellite L300 running 12.04. When plugged, it gives an error 

> Error mounting: mount: /dev/sdb1 already mounted or /media/Babby busy

The disk utility shows two peripheral devices(16GB harddisk and Sandisk Cruzer). I run "dmsetup remove_all" and the 16GB harddisk disappears, leaving me to mount the SanDisk. The problem is I have to repeat the process every time I plug the pendrive. Strangely all the Ubuntu systems mount the pendrive fine. Is there any permanent fix?

---

