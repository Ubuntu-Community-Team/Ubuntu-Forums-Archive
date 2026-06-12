---
title: "External HDD wont ever mount"
date: 2010-08-15
forum: General Help
---

### Post by James_N on 2010-08-15
Hi All,

Ive had this problem in Linux for ages. Every so often I keep going back to linix hoping to get my external HDD to work in linux, but it always fails. Ive tried in Ubuntu, and this time, I was trying from a Mint 9 live image.

This is my problem:

[img]http://www.jnolan.co.uk/Screenshot.png[/img]

and this is the output from fdisk -l

> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004548e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6375    51097600    7  HPFS/NTFS
/dev/sda3            6375       12749    51200000    7  HPFS/NTFS
/dev/sda4           12749       60802   385984512    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002093a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976761560    7  HPFS/NTFS
mint@mint ~ $ 


A few things to note:

It sees all my internal NTFS partitions fine.

As per instructions on other topics, ive run chkdsk from windows on the drive twice, and always used the "safely remove this drive from windows" button, so its always been removed properly.

Really need to keep the drive as NTFS because A) it has a lot of stuff on it and B) the rest of my family have only just got the hang of windows, let alone Linux!

Hoping some people here can help me, because everything ive tried over the years just hasn't worked, and linux would be ideal for my needs as i only email / surf the net, so the need to ditch windows and switch to something free would be nice.

Thanks as always folks
James

---

