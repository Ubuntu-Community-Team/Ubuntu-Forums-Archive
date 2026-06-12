---
title: "Unable to Change UUID of Partition"
date: 2010-07-01
forum: General Help
---

### Post by jcobban on 2010-07-01
I am trying to maintain a backup of my system using a duplicate SATA 250MB drive in a USB enclosure, which I cloned from the drive in my computer.  The problem is that:
[LIST=1]
[*]Automount doesn't work when I plug in the drive because the UUID is a duplicate of the UUID on the ext4 partition on my main drive.
[*]If I try 'mount /dev/sdc5' it complains that the partition is already mounted at /.
[*]If I add a 'mount by label' entry in the fstab the system complains during boot if I have not got the USB drive plugged in.
[*]If I plug the drive in before booting I cannot 'umount' the drive.
[/LIST]
So I tried following the procedure for explicitly changing the UUID of the partition:
 
```
$ sudo fdisk -l
[sudo] password for jcobban: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78e93ce5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           29003       30401    11236352    7  HPFS/NTFS
/dev/sda3               1       29002   232958533+   5  Extended
/dev/sda5               1       28584   229600917   83  Linux
/dev/sda6           28585       29002     3357553+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78e93ce5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18866   151541113+   7  HPFS/NTFS
/dev/sdc2           29003       30401    11236352    7  HPFS/NTFS
/dev/sdc3           18867       29002    81417420    5  Extended
/dev/sdc5           18867       28584    78059803+  83  Linux
/dev/sdc6           28585       29002     3357553+  82  Linux swap / Solaris

Partition table entries are not in disk order

$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2010-07-01 10:37 34E0E317E0E2DE5C -> ../../sdc1
lrwxrwxrwx 1 root root 10 2010-07-01 10:37 64E2185EE2183730 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2010-07-01 10:37 f0a635ba-d2e2-491f-9984-e87d75077a6b -> ../../sdc6
lrwxrwxrwx 1 root root 10 2010-07-01 10:37 f81f4681-6cb9-46e7-9262-d5f57c723774 -> ../../sdc5

$ uuidgen
72fe2e64-bfe3-4019-936b-66a5f57a9061

$ tune2fs /dev/sdc5 -U 72fe2e64-bfe3-4019-936b-66a5f57a9061
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Permission denied while trying to open /dev/sdc5
Couldn't find valid filesystem superblock.

```
Any suggestions on how to get this to work?

---

