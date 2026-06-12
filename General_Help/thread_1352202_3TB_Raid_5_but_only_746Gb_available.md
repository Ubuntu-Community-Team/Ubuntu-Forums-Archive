---
title: "3TB Raid 5 but only 746Gb available"
date: 2009-12-11
forum: General Help
---

### Post by jamessbull on 2009-12-11
Hi,

I've got 3 1.5 Tb western digital disks. 

I decided I wanted to put them in RAID 5 using software raid

I installed mdadm. I opened the palimpset disk utility and used that to create a new software reid array using those disks.

First it said the array was degraded and was rebuilding x% etc.

So I left that running over night. Today the computer was still running and had a lovely new raid array of 3001Gb so I created a FAT file system on there.

In palimpset this says
3001 GB /2795 GiB ...
FAT(32bit version) file system
Not partitioned

I mounted this and that operation completed successfully. I now had the drive in the file explorer. 

Now for the problem - When I right click properties in there it tells me I have 749 Gb available. I copied some stuff to it and that worked fine and the amount of free space went down.

Whats going on?

---

### Post by benjaminsuman on 2009-12-11
I'm not entirely sure what is going on, but you shouldn't be using FAT for a file system that large.  Extremely large FAT volumes become inefficient and fragment quickly.  You really should consider EXT4 or XFS instead.

---

### Post by cascade9 on 2009-12-11
3001 GB is right. So, I would guess that its a Fat32 partition size problem. I'm not sure why its gone to 746GB, but you wont be able to make a 3TB partition with Fat32-

> **Note:** I am not really sure what the maximum partition size is for a FAT32 partition. :^) I have heard various different numbers, but nobody seems to be able to produce an authoritative answer. "Officially" it is 2,048 GiB (2 TiB), but there are likely to be other limiting factors...

[http://www.pcguide.com/ref/hdd/file/partFAT32-c.html](http://www.pcguide.com/ref/hdd/file/partFAT32-c.html)

Considered trying a different file system? Fat32 is, well, very old and pretty crap.

---

### Post by jamessbull on 2009-12-12
> **cascade9 said:**
> 3001 GB is right. So, I would guess that its a Fat32 partition size problem. I'm not sure why its gone to 746GB, but you wont be able to make a 3TB partition with Fat32-



[http://www.pcguide.com/ref/hdd/file/partFAT32-c.html](http://www.pcguide.com/ref/hdd/file/partFAT32-c.html)

Considered trying a different file system? Fat32 is, well, very old and pretty crap.

xfs didn't want to work so I did ext4 instead and that did work.

Hooray!

---

### Post by cascade9 on 2009-12-13
Cool, it was just a fat32 issue. *notes this for future reference*

Good to hear its working right now ;)

---

