---
title: "Extended partition stuff"
date: 2009-12-17
forum: General Help
---

### Post by cr0bar on 2009-12-17
So, I deleted a primary partition I was using as storage, but I've since decided to leave that to my external drive instead. The ~100GB partition I was planning on using for messing with different distros. I however can't create any partitions it seems using Disk Utility.

[img]http://i45.tinypic.com/23i8qdg.png[/img]

This is how it looks in Disk Utility..

[http://pastebin.ca/1718843](http://pastebin.ca/1718843)

This is what I get when I try to create any sort of partition in the unallocated space after the 1KB one.

-e-

I also can't remove the 1KB extended one either by clicking on delete.

I'm doing something wrong here, but since I am new to partitioning within Linux I'm not sure exactly what it is.

---

### Post by dcstar on 2009-12-17
> **cr0bar said:**
> So, I deleted a primary partition I was using as storage, but I've since decided to leave that to my external drive instead. The ~100GB partition I was planning on using for messing with different distros. I however can't create any partitions it seems using Disk Utility.

[img]http://i45.tinypic.com/23i8qdg.png[/img]

This is how it looks in Disk Utility..

[http://pastebin.ca/1718843](http://pastebin.ca/1718843)

This is what I get when I try to create any sort of partition in the unallocated space after the 1KB one.

-e-

I also can't remove the 1KB extended one either by clicking on delete.

I'm doing something wrong here, but since I am new to partitioning within Linux I'm not sure exactly what it is.

a) You can only have 4 Primary Partitions **maximum** (including an Extended partition).

b) You can have as many partitions as you like in an Extended Partition.

c) You must unmount any partition you want to delete.

d) You cannot create any sort of filesystem in a 1K partition - it is just too small.

---

### Post by cr0bar on 2009-12-17
Thanks for the prompt reply.

When I try and delete the 1KB partition, it gives me this:

[http://pastebin.ca/1718876](http://pastebin.ca/1718876)

---

### Post by Leppie on 2009-12-17
> **dcstar said:**
> a) You can only have 4 Primary Partitions **maximum** (including an Extended partition).

there can be only 1 extended partition on a disk, there's already 1 on the disk so only primary partitions can be added.

are you using the disk utility with admin access? most disk utilities require admin access.

---

### Post by cr0bar on 2009-12-17
> **Leppie said:**
> there can be only 1 extended partition on a disk, there's already 1 on the disk so only primary partitions can be added.

are you using the disk utility with admin access? most disk utilities require admin access.

Unfortunately it still gives me that same error trying to delete the 1KB partition when I did "sudo palimpest" in terminal.

As regards only one extended partition being on a disk, would it just be simpler to format the drive and reinstall Ubuntu, and prepare a couple of 20GB partitions inside the extended one for other distros, and then have the primary Windows one at the end?

---

### Post by Leppie on 2009-12-17
try using gparted (gui) or fdisk (cli).

maybe use the space of the current extended partition as a shared partition.
then create the extended partition at the end of the disk where the free space is located now.

---

