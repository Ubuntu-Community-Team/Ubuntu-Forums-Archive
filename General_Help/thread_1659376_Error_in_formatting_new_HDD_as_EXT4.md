---
title: "Error in formatting new HDD as EXT4 ?"
date: 2011-01-03
forum: General Help
---

### Post by albertwt on 2011-01-03
Hi All,

I'm having problem in formatting the newly added hard drive to my Ubuntu 64 bit server, is there any explanation why I got stuck to this error ?

```
root@isuzu:~# fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00025338

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        2611    20719617    5  Extended
/dev/sda5              32        2611    20719616   8e  Linux LVM

Disk /dev/sdb: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc618204

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2610    20964793+   5  Extended

```
and here's the result:

```
root@isuzu:~# mkfs -t ext4 /dev/sdb1
mke2fs 1.41.11 (14-Mar-2010)
mkfs.ext4: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).

```

I've followed the instruction in this: ```
https://help.ubuntu.com/community/InstallingANewHardDrive
```

but I want to use the latest Ext 4 FS for all of my newly deployed VM

Cheers,

Albert

---

### Post by hawkmage on 2011-01-03
The partition sdb1 you defined as "Extended".  An "Extended" partition is basically a container and it can not hold a filesystem.

---

### Post by albertwt on 2011-01-03
> **hawkmage said:**
> The partition sdb1 you defined as "Extended".  An "Extended" partition is basically a container and it can not hold a filesystem.

ah.. so in this case i must re do all of the FDISK command to make it as primary ?

---

### Post by hawkmage on 2011-01-03
No, you can fdisk and add a logical partition and make it of type "Linux"

---

### Post by albertwt on 2011-01-03
> **hawkmage said:**
> The partition sdb1 you defined as "Extended".  An "Extended" partition is basically a container and it can not hold a filesystem.

```
root@isuzu:~# fdisk /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the DOS compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): n
[B]Command action
   l   logical (5 or over)
   p   primary partition (1-4)
l
First cylinder (1-2610, default 1): 1
Last cylinder, +cylinders or +size{K,M,G} (1-2610, default 2610): 2610[/B]

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
**_root@isuzu:~# mkfs -t ext4 /dev/sdb1_**
[B]mke2fs 1.41.11 (14-Mar-2010)
mkfs.ext4: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).[/B]
```

yes and it is still failed :-|

seethe above error ?

---

### Post by hawkmage on 2011-01-04
sdb1 is still the extended partition, the logical partition should be /dev/sdb5.  Try mkfs -t ext4 /dev/sdb5.

My partitions look like this:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         249     2000061   82  Linux swap / Solaris
/dev/sda2             250       30401   242195940    5  Extended
/dev/sda5           30340       30401      498015   83  Linux
/dev/sda6             250       30338   241689829+  83  Linux
```

---

### Post by albertwt on 2011-01-04
> **hawkmage said:**
> sdb1 is still the extended partition, the logical partition should be /dev/sdb5.  Try mkfs -t ext4 /dev/sdb5.

My partitions look like this:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         249     2000061   82  Linux swap / Solaris
/dev/sda2             250       30401   242195940    5  Extended
/dev/sda5           30340       30401      498015   83  Linux
/dev/sda6             250       30338   241689829+  83  Linux
```

hm.. may I know what's the command to display the information above please ?

---

### Post by albertwt on 2011-01-04
here's what it looks like:

> root@isuzu:~# fdisk -l

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00025338

			   Device Boot      Start         End      Blocks   Id  System
			/dev/sda1   *           1          32      248832   83  Linux
			Partition 1 does not end on cylinder boundary.
			/dev/sda2              32        2611    20719617    5  Extended
			/dev/sda5              32        2611    20719616   8e  Linux LVM

Disk /dev/sdb: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc618204

			   Device Boot      Start         End      Blocks   Id  System
			/dev/sdb1               1        2610    20964793+   5  Extended
			/dev/sdb5               1        2610    20964762   83  Linux

---

### Post by hawkmage on 2011-01-04
The partition list shoes the Linux partition on the new drive to be /dev/sdb5 did you try the command:
```
mkfs -t ext4 /dev/sdb5
```

---

### Post by albertwt on 2011-01-06
> **hawkmage said:**
> The partition list shoes the Linux partition on the new drive to be /dev/sdb5 did you try the command:
```
mkfs -t ext4 /dev/sdb5
```

yes that works for me.

Thanks man !!!

---

### Post by ErayT on 2012-08-02
> **albertwt said:**
> ```
root@isuzu:~# fdisk /dev/sdb

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the DOS compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): n
[B]Command action
   l   logical (5 or over)
   p   primary partition (1-4)
l
First cylinder (1-2610, default 1): 1
Last cylinder, +cylinders or +size{K,M,G} (1-2610, default 2610): 2610[/B]

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
**_root@isuzu:~# mkfs -t ext4 /dev/sdb1_**
[B]mke2fs 1.41.11 (14-Mar-2010)
mkfs.ext4: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).[/B]
```

yes and it is still failed :-|

seethe above error ?

Dude I wonder why do you have a section of creating a logical partition in fdisk whereas I do not. When I run fdisk to create a partition, I have two options extended and primary.

---

