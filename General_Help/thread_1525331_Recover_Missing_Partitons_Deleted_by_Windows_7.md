---
title: "Recover Missing Partitons Deleted by Windows 7"
date: 2010-07-06
forum: General Help
---

### Post by palian on 2010-07-06
I want to recover my 'Home' and 'Storage' partitions and the data they contain which no longer show up in Gparted. 

I have a 320gb hard drive as my primary where originally (from right to left in Gparted):

[INDENT][LIST=1]
[*]80g NTFS XP primary partition
[*]240g Extended partition
[/LIST][/INDENT]
[INDENT][INDENT][LIST=1]
[*]180g EXT3 'Storage' Logical partition
[*]     40g EXT3 'Home' Logical partition
[*]     16g EXT3 '/' Logical partition
[*]     4g  SWAP Logical partition
[/LIST][/INDENT][/INDENT]

I upgraded XP to Windows 7. Using the disk manager utilities that is part of the windows 7 install I deleted the old 80g NTFS partition to split it into two 40g partitions (an OS partition and general partition). Intended disk configuration:

[INDENT][LIST=1]
[*]40g NTFS Win7 OS primary partition
[*]40g NTFS Win7 Storage  primary partition
[*]240g Extended partition
[/LIST][/INDENT]
[INDENT][INDENT][LIST]
[*]180g EXT3 'Storage' Logical partition
[*]40g EXT3 'Home' Logical partition
[*]16g EXT3 / Logical partition
[*]4g  SWAP Logical partition
[/LIST][/INDENT][/INDENT]

I noticed that what was once 'Storage' and 'Home' was now 220g of unallocated space when I booted up the Ubuntu 10.04 live cd on a USB. 

[INDENT][LIST=1]
[*]40g NTFS Win7 OS primary partition
[*]40g NTFS Win7 Storage primary partition
[*]240g Extended partition
[/LIST][/INDENT]
[INDENT][INDENT][LIST]
[*]220g unallocated space
[*]16g EXT3 / Logical partition
[*]4g  SWAP Logical partition
[/LIST][/INDENT][/INDENT]

How should I go about recovering the partitions and the data they contained?

Lucky, the '/' partition is still recognized and the /etc/fstab file contains the original disk partitioning information. I also have a back up of the old MBR I made with 'Ghost 4 Linux'.

---

### Post by ajgreeny on 2010-07-06
Have a look at testdisk, which you can install in your ubuntu root as normal as it is other partitions you have lost.

I've never used it personally, but many others have, and as long as you have written nothing to those old, now newly formatted partitions, you should be able to find the old partition table and restore them as they were.

---

