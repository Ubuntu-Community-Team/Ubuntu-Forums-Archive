---
title: "Changed format to master boot record. Can't mount drive."
date: 2011-03-09
forum: General Help
---

### Post by tmandpea on 2011-03-09
hello, so I have a 1TB hard drive which is formatted with FAT32.

Attempting to make a new partition I clicked the format drive button in Disc Utility.

I chose Master Boot Record and something was written to the drive.

So now I can't mount the drive and Disc Utility says that there aren't any partitions.
I don't think this can be true because I had 200 GB of data on the drive and it would have taken longer to delete all that. At least I think...

Can anyone help? :confused:

---

### Post by tmandpea on 2011-03-09
Since I can't mount the drive I cant use any programs that would help me bring the partition back...

bump

---

### Post by tmandpea on 2011-03-09
So I tried using Testdisk.

It said there were no partitions also.

see attached

---

### Post by srs5694 on 2011-03-09
There are two levels of data structures on most hard disks:


[list]
[*]**The partition table** -- This defines the way the disk is "sliced up" for use by different operating systems or for different purposes by a single OS. The Master Boot Record (MBR) partition table is the most common type of partition table on PCs, but there are others. A partition table can define from one to many individual partitions. ("Many" can theoretically be billions, but in practice few disks have more than a dozen or so partitions.)
[*]**The filesystem** -- This is a data structure that usually resides on a single partition. It stores individual files by name, organized in directories. FAT, NTFS, ext2fs, ext3fs, ext4fs, ReiserFS, JFS, and XFS are examples of filesystems. Although not technically a filesystem, Linux swap space is similar in where it fits on the disk-use hierarchy.
[/list]


Your disk had a FAT32 filesystem, which was probably in a partition, although some disks come with FAT filesystems written to the disk without the benefit of a partition table. When you told Disk Utility to create a new MBR partition table, it erased the old one, including all record of the filesystem you had before. Disk Utility can do this by writing a few bytes to the disk; there's no need to erase every file on the disk, but they'll still be lost.

All hope is not lost, though. If you didn't create a new filesystem, you may be able to recover the old partition using [TestDisk.](http://www.cgsecurity.org/wiki/TestDisk) This tool scans for filesystem signatures and creates a new partition table to hold what it finds (or it adds filesystems in partitions it adds to an existing partition table).

Assuming you can recover your old partition and its data, you should use Disk Utility, GParted, or some other tool to discover if that partition covers the whole disk. If it does, you'll need to resize it before you can add a new partition. GParted can do this (I'm not sure about Disk Utility), but you should be aware that partition resizing is inherently dangerous. Thus, you should back up your data before you attempt it. With the partition resized, you can create a new partition in the empty space. You should *not* attempt to create a new partition table, though -- doing so normally deletes the existing partitions in (literally) less than a heartbeat. (Some in-place conversions between partition table formats are possible with certain tools and are therefore exceptions to this rule, but based on your description, you don't need to do this at this time.)

---

### Post by srs5694 on 2011-03-09
> **tmandpea said:**
> So I tried using Testdisk.

It said there were no partitions also.

You posted just as I began composing my reply. TestDisk supports a couple different levels of analysis. Proceed through its menus and you'll find an option for doing a deeper scan. Select it. With any luck it'll find your old partition.

If that fails, your best bet is [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which scans for and recovers individual files; however, chances are you'll lose filenames and directory structure, so you'll end up spending a lot of time sorting through and renaming the files you recover.

---

### Post by tmandpea on 2011-03-10
Thanks for the fantastic reply.

I've been doing a deeper scan for an hour now...1TB takes a long time to scan, but I'll let it run tonight and see if it picks up the old partition.

If I understand correctly Disc Utility just clipped the partition making it unreadable but the data is still there waiting to be overwritten, correct?

---

### Post by srs5694 on 2011-03-10
> **tmandpea said:**
> If I understand correctly Disc Utility just clipped the partition making it unreadable but the data is still there waiting to be overwritten, correct?

Essentially, yes, *if* you didn't create a new partition (or more importantly, a new filesystem) in its place and *if* the disk was partitioned to begin with (an uncommon arrangement is to put a filesystem directly on a disk without a partition table).

Normally, if a disk had just a single partition, TestDisk should discover that partition pretty quickly and tell you it's found it, although the program might take a while to scan the rest of the disk. If it hasn't indicated that it's found something, it's quite possible that it won't, most probably because of one of those two caveats.

---

### Post by tmandpea on 2011-03-10
So unfortunately testdisk crashed after it was finished searching the drive... I'll try again later today

In the meantime I've been trying various programs to see if I can restore the partition table.

Here's gparted:

I really don't want to give up hope here but it seems that I wont be able to restore the partition and files on it.

---

