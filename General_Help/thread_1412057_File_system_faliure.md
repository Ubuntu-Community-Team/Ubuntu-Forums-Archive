---
title: "File system faliure"
date: 2010-02-20
forum: General Help
---

### Post by tiddlydum on 2010-02-20
Recently, my laptop reached critical battery and hibernated. However, on wake, it died. When it rebooted, I got fsck output, and half of my partition appears to be unreadable. I have access to network drives and have backed up my ubuntu, but the problem has spread to my win 7 partition. Palimpsest (the disk utility) is reporting that my drive has 61 bad sectors. What should I do?

---

### Post by quixote on 2010-02-22
Sounds like it didn't hibernate correctly and maybe overwrote some sectors.  Linux actually writes the equivalent of a File Allocation Table at several places on the partition, and fsck, or better e2fsck, or [testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") can recover from those.  The first two only work on linux partitions.  Testdisk works on any type, including windows.

Important: never run either of those on a drive that's in use ("mounted").  Boot from a liveCD and unmount the drive, if it's mounted, before doing anything.

Before getting into details: it's a bit disturbing that you say the problem is "spreading" to the Windows partition.  That sounds to me more like a failing hard drive, since a linux filesystem corruption would stay entirely within the linux partition.  If it is a failing drive, you want to reduce disk accesses as much as possible until you have all the data you want backed up to another drive.

Okay, on to some details.  

e2fsck is always available, but testdisk needs to be temporarily installed via the liveCD if you want to use it.  If you decide to try that, I can give you the step-by-step on how to do that.  To see the instructions on how to use e2fsck, type in a terminal (Applications > Accessories > Terminal)```
man e2fsck
```It's a lot to plow through, but it's worth skimming to get oriented.

So, what you might try after booting from a livecd, and making sure the target drive is not mounted, is ```
sudo e2fsck -p /dev/*[COLOR="Blue"]target-partition[/COLOR]*
``` To find the target designation if you don't know it, you can use ```
sudo fdisk -l   *("l" as in list)*
```and figure out from the size and filesystem type which one is your linux partition.

Hope this helps.

---

