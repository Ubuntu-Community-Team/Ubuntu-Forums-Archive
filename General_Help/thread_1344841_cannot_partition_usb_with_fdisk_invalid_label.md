---
title: "cannot partition usb with fdisk? invalid label?"
date: 2009-12-03
forum: General Help
---

### Post by gobbledigook on 2009-12-03
Hi!

i recently got a new 8gb usb to put opt-ware onto my router... i was using a 2gb stick but it was the wrong shape and didn't fit correctly... so i tried to dd the partion table and data over, but it didn't work! can't remember the exact error now, but here is the problem... now i cannot repartition it using gparted or fdisk! here is some terminal output:
```

dan@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8.1.159-1e0e
======================
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label
^C
dan@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32c932c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders
Units = cylinders of 16 * 512 = 8192 bytes
Disk identifier: 0xffffffff

Disk /dev/sdb doesn't contain a valid partition table
dan@ubuntu:~$ sudo fdisk /dev/sdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xe4b40fb8.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): o
Building a new DOS disklabel with disk identifier 0xf2f51ddc.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
dan@ubuntu:~$ sudo fdisk /dev/sdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xb1938f12.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): v
16383 unallocated 512-byte sectors

Command (m for help): p

Disk /dev/sdb: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders
Units = cylinders of 16 * 512 = 8192 bytes
Disk identifier: 0xb1938f12

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): o
Building a new DOS disklabel with disk identifier 0x8baea4eb.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): p

Disk /dev/sdb: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders
Units = cylinders of 16 * 512 = 8192 bytes
Disk identifier: 0x8baea4eb

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (2-1024, default 2): 
Using default value 2
Last cylinder, +cylinders or +size{K,M,G} (2-1024, default 1024): 
Using default value 1024

Command (m for help): p

Disk /dev/sdb: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders
Units = cylinders of 16 * 512 = 8192 bytes
Disk identifier: 0x8baea4eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        1024        8184   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
dan@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8.1.159-1e0e
======================
/dev/sdb: unrecognised disk label
```


have i completely broken it?? any ideas guys!!??

---

### Post by Chame_Wizard on 2009-12-03
You have to format,since the size is 8 MiB only instead of 8 GiB!!!:o

---

### Post by gobbledigook on 2009-12-03
hey:)

thanx for your reply... but i cannot create a valid partition table!

using fdisk:

```

dan@ubuntu:~$ sudo fdisk /dev/sdb1

Unable to open /dev/sdb1
dan@ubuntu:~$ sudo fdisk /dev/sdb

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
e
Partition number (1-4): 1
First cylinder (2-1024, default 2): 
Using default value 2
Last cylinder, +cylinders or +size{K,M,G} (2-1024, default 1024): 
Using default value 1024

Command (m for help): p

Disk /dev/sdb: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders
Units = cylinders of 16 * 512 = 8192 bytes
Disk identifier: 0x50f0d6d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        1024        8184    5  Extended

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

but after /dev/sdb1 doesn't exist!

```
dan@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 8 MB, 8388608 bytes
1 heads, 16 sectors/track, 1024 cylinders
Units = cylinders of 16 * 512 = 8192 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

i have also tried:
```
dan@ubuntu:~$ sudo mkfs.vfat /dev/sdb1
mkfs.vfat 3.0.3 (18 May 2009)
/dev/sdb1: No such file or directory
dan@ubuntu:~$ sudo mkfs.ext3 /dev/sdb1
mke2fs 1.41.9 (22-Aug-2009)
Could not stat /dev/sdb1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
dan@ubuntu:~$ sudo mkfs.ext3 /dev/sdb
mke2fs 1.41.9 (22-Aug-2009)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) n
dan@ubuntu:~$ sudo mkfs.vfat /dev/sdb
mkfs.vfat 3.0.3 (18 May 2009)
mkfs.vfat: Device partition expected, not making filesystem on entire device '/dev/sdb' (use -I to override)

```

---

### Post by dcstar on 2009-12-03
Use gparted to write a new partition table to the device.

---

### Post by gobbledigook on 2009-12-17
Hi! 

sorry for leaving this so long to sort out!! i've been busy with other stuff :(

@ dcstar: please refer to my initial post - the first part of terminal output is from running gparted from cli... whe i try and do anything with gparted it just errors: 
```
dan@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8.1.159-1e0e
======================
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label
/dev/sdb: unrecognised disk label
```

any other ideas anyone? am i missing something here!?! do i need to reboot after using fdisk to create partition table? there is no data to lose on this flash device so anything that just gets it back would be appreciated :)

thanx!

Dan

---

### Post by gobbledigook on 2009-12-18
*bump*

---

### Post by dcstar on 2009-12-19
> **gobbledigook said:**
> 
........
any other ideas anyone? am i missing something here!?!
........


The device may now be faulty.

---

### Post by gobbledigook on 2009-12-21
i am slowly coming to the conclusion that i must have broken this beyond repair :( oh well... flash is cheap these days ;)

---

