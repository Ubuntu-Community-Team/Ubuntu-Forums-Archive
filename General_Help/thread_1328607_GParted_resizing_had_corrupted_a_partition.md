---
title: "GParted resizing had corrupted a partition"
date: 2009-11-16
forum: General Help
---

### Post by troy.mcclure on 2009-11-16
Hi All,

I was running Karmic 64bit, and wanted to install a 32 bit version.
**I've resized a partition with GParted**, shrank it with 20GB. It was previously mounted to /home.

[B]All partitions are ext4, and I'm on RAID0 using my Intel's ICH9R.

[/B]After shrinking and installing the 32 bit karmic on the new partition, the old /home partition isn't accessible.

[B]fsck.ext4 /dev/mapper/isw_bahdiiijae_Volume06 (the problematic partition) returned:

The filesystem size (according to the superblock) is 46026217 blocks
The physical size of the device is 40905498 blocks
Either the superblock or the partition table is likely to be corrupt![/B]

I know that the physical size is "right", since it's after the shrink. The superblocks see the data before the shrink.

I have done many tryings and google searches, and nothing helped.
I didn't manage getting testdisk, fsck, fsck.ext4, resize2fs nor e2fsck to work.
Also, all my tries to find how to change the size of the disk as the filesystem thinks it is, have failed.

**Please, help me save my dear /home!**

---

### Post by hwttdz on 2009-11-16
What about refreshing the partition table?  
[http://linux-tipps.blogspot.com/2009/02/refresh-partition-table.html](http://linux-tipps.blogspot.com/2009/02/refresh-partition-table.html)

Have you rebooted since?

---

### Post by Giblet5 on 2009-11-16
You did a backup first, right?

You can try using gparted to undo what you did (return that filesystem to its EXACT original size), but I'm skeptical that you will recover anything.

Problem 1: Software raid is the short path to data loss. But it's cheap, so there's all that money to roll around in when the data disappears. RAID is great. Software RAID is not RAID - it's a cheap knockoff of RAID which is hardware RAID.

Problem 2: Anytime you do something at all significant to your system (like moving partitions around), do a backup first.

I hope the gparted resize works. Let us know so that it's documented. Because someone else might do this someday.


> **hwttdz said:**
> What about refreshing the partition table?  
[http://linux-tipps.blogspot.com/2009/02/refresh-partition-table.html](http://linux-tipps.blogspot.com/2009/02/refresh-partition-table.html)

Have you rebooted since?

OP says fsck sees the correct physical size (partition table is updated) but the superblock was not updated for the new size.

If it were my system, I would repair the superblock with a tool I wrote. I don't know another way to edit ext4 filesystem structure that's accessible to an Ubuntu user though.

---

### Post by troy.mcclure on 2009-11-16
Thanks for your replies.

Well, 

**blockdev --rereadpt /dev/mapper/isw_bahdiiijae_Volume06**

returned  **BLKRRPART: Invalid argument**
(everything as root of course)

GParted will no longer negotiate with me regarding this partition. No matter what I'm trying to do with it, GParted returns the error I've posted (regarding FS size/physical size mismatch).

Thanks again, and in advance.

---

### Post by troy.mcclure on 2009-11-16
As for rebooting, I've rebooted many times. I'm working on this problem for almost straight 72 hours. But, I'm not such an expert on Linux, especially on all FS issues.

Gilbert, maybe I can use your tool?

---

### Post by Giblet5 on 2009-11-16
Sorry, it's not ready for general use and it requires in-depth knowledge of linux filesystems anyway.

I'm just guessing here, but I suspect that gparted doesn't work with ext4 raid partitions.

I would leave the partitions alone and open a launchpad bug report against gparted. The developer may have a trick or three up his sleeve and your bug report will help him decide whether your partition can be salvaged.

I'm very sorry this happened to you. I hope you get a quick and easy fix.

---

### Post by troy.mcclure on 2009-11-16
Thanks Giblet.

Let's hope prayers and developers will help.

---

