---
title: "what is mount point,swap partition and partition?"
date: 2012-03-28
forum: General Help
---

### Post by jeshrel on 2012-03-28
Hi,I would like to know in detail what is mount point,swap partition and partition?Thank you

---

### Post by yetiman64 on 2012-03-28
[[COLOR=Blue]--Mount point--[/COLOR]]("http://www.linfo.org/mount_point.html")  (link to info source)

> A *mount point* is a directory (typically an empty one) in the currently accessible filesystem on which an additional filesystem is *mounted* (i.e., logically attached). [[COLOR=Blue]--swap partition--[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")  (link to info source)
[COLOR=Blue] 
[/COLOR]> [SIZE=2]What is swap?[/SIZE] 
Swap space  is the area on a hard disk which is part of the Virtual Memory of your  machine, which is a combination of accessible physical memory (RAM) and  the swap space. Swap space temporarily holds memory pages that are  inactive. ...<snip for brevity>... Swap space can be a dedicated swap partition (recommended), a swap file, or a combination of swap partitions and swap files. [[COLOR=Blue]--partition--[/COLOR]]("http://en.wikipedia.org/wiki/Disk_partitioning")  (link to info source)

> **Disk partitioning** is the act of dividing a hard disk drive into multiple logical storage units referred to as *partitions*, to treat one physical disk drive as if it were multiple disks. Partitions are also termed "slices" for operating systems based on BSD, Solaris or GNU Hurd. A partition editor software program can be used to create, resize, delete, and manipulate these partitions on the hard disk.Please use the blue links to read the original source for the above quotes. Cheers.

---

### Post by Vaphell on 2012-03-28
partition is a subset of hdd space that acts as an independent entity. You can have 1 or more partitions on hdd. If in windows you got C: D: E: ... that are not optical drives, these are partitions.

Swap is a kind of partition used as a temporary cache for things swapped out of ram, you know, ram usage gets high and hdd starts thrashing :-)

mount points are places in logical structure of system where physical disk partition is to appear.
mount point is a location in system directory tree where the physical partition is to be plugged in. in windows the partition structure is painfully obvious - partitions are at the top level c: d: ..., while in linux it's all abstracted away. You have only one system tree and you can plug anywhere, eg /home/my_user_name/Documents/my_top_secret_stuff. That means that the partition mounted in that place acts as a directory with that exact path and it's all seamless (at least in theory)

---

### Post by CharlesA on 2012-03-28
The two previous posters pretty much covered it.

I'm curious tho, is this a homework question?

---

