---
title: "Second Partition?"
date: 2011-03-01
forum: General Help
---

### Post by Enzo. on 2011-03-01
Hello I've installed Ubuntu 10.10 30 mins ago

And I formated my logical partition into ext2. And my storage partition was in ntfs. Now it's not displayed in Disk Usage Analyzer, what to do?

And how to get it back visual without losing files?

THank you

---

### Post by mastablasta on 2011-03-01
did you try the live CD to see if the system work before installing it?
 
Why did you use ext2?
 
to get the ntfs partition displayed you need to mount it first. go to places. find it and click on it to mount. then start the disk analyzer.

---

### Post by Enzo. on 2011-03-01
Already mounted it, didnt seen it :)

Well I Used ext2 Because I couldnt install with ntfs format.

---

### Post by seawolf167 on 2011-03-01
> **mastablasta said:**
> Why did you use ext2?
> **Enzo. said:**
> Well I Used ext2 Because I couldnt install with ntfs format.

I think he meant why not use ext3 or the new[er] ext4?

---

### Post by Topsiho on 2011-03-01
Let me guess:

You installed Ubuntu in a logical partition, which was formatted to ext2.
This might indicate that your ntfs-partition is in a primary partition, probably /sda1 (first partition on the drive), and the ext2-partition will be in /sda5 (first logical partition).

If you have installed like this your files, which were in /sda1, must be fine, if you defragmented your C:\ drive in windows (several times), and after that made room to receive the Ubuntu install.

If so, then you should be able to find your files in Location, as was said before, > Computer (I cannot test this as I have a full Linux install here).

ext2 is very obsolete, better is to use ext3, or even better, ext4, which are newer, and are journaling, which means they can recover lost data (they keep a "journal" of the last entries).

If you decide to reinstall, better save all your personal data that you would hate to lose, and create more primary and/or logical partitions, keeping in mind that 4 is the limit for the number of primary partitions on a disk.

1. a partition for the system files, ext4, mountpoint /, at least about 5GiB, better more, say 10 or 15, disk space permitting, and 2. for your personal files, ext4, mountpoint /home, as much as diskspace permits (one never has enough!).
Create also a swap file (type swap), usually one uses 2 times RAM-memory space (working memory in computer). Here data is temporarily stored when working memory space gets all used up, effectively extending the working memory, but slowing down the computer quite a bit (I almost said fast :) ).

Hope this helps :)

A storage partition in ntfs is only useful if the files must be available in both windows and Linux, as Linux can read ntfs files, while windows can't read Linux files. As far as I know Linux nowadays can even write files in ntfs out of the box.

Topsiho

---

