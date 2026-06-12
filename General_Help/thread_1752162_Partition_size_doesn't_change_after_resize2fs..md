---
title: "Partition size doesn't change after resize2fs."
date: 2011-05-07
forum: General Help
---

### Post by wbuntu on 2011-05-07
I did
e2fsck -f /dev/sdb1
resize2fs /dev/sdb1
e2fsck -f /dev/sdb1
Partition size didn't change "df -h", however cylinders did change when i checked "fdisk -l".
how can i fix it?
thanks

---

### Post by srs5694 on 2011-05-07
First, you must understand the differences between three key data types/structures:


[list]
[*]**Cylinders** -- The number of "cylinders" on a disk, as reported by fdisk, is a fiction that was convenient at one time but is today largely irrelevant and even distracting. Spinning disks *do* have an underlying true number of cylinders, but the values used by fdisk and other disk partitioning tools are based on a lie told to them by the hard disk or computed in other ways. They used to be required to do cylinder/head/sector addressing of the hard disk, but CHS maxes out at a bit under 8 GiB, so it's not used much today, although it's still supported by many tools. Today, LBA mode, which uses a single sector value, is used instead of CHS mode and its three values.
[*]**Partitions** -- These are defined in the disk's partition table, and they can only be changed by editing the partition table with fdisk, parted, GParted, gdisk, or some other partition-editing tool. The partition table is a fairly simple data structure; it need only define the start and end points (or start points and sizes) of various partitions, along with some convenient metadata such as partition type codes.
[*]**Filesystems** -- These are much more complex data structures that reside *inside* partitions (or sometimes inside other data structures, such as logical volumes in an LVM configuration or even inside files if you're using a virtual environment or create a disk image backup). The size of a filesystem is somewhat independent of the size of its carrier partition; a filesystem can be smaller than a carrier partition, but if the filesystem is larger than the carrier partition, that's an error.
[/list]


The resize2fs program operates on filesystems, not on partitions. Used in the way you used it, it resizes the filesystem to completely fill the carrier partition. (Note that in Ubuntu, all of these commands would normally need to be preceded by "sudo" to work.) It should not touch the partition table itself, though. Thus, I'm not at all surprised that "df -h" didn't show a change; this would be perfectly normal if the filesystem was already properly sized for its partition. I am surprised that the number of cylinders changed when you checked with fdisk, though; since resize2fs doesn't modify the partition table, the cylinder count shouldn't have changed. Perhaps something else is causing your CHS geometry to change, though.

If you want to resize your partitions *and* the filesystems they contain, the usual solution in Linux is to use GParted, which presents a user interface that enables you to do both simultaneously. If you don't want to use GParted, the usual solution is to use fdisk (or gdisk for GPT disks) to delete the partition and recreate it with a larger size, and then use resize2fs to resize the filesystem it contains; or to use them in the opposite order to shrink a partition and its filesystem. Either way, the fdisk/resize2fs combination provides a much greater chance for human error to creep in and cause problems, so GParted is definitely the preferred way to do this.

---

