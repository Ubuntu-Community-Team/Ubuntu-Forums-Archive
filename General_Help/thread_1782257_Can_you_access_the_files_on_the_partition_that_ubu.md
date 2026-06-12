---
title: "Can you access the files on the partition that ubuntu is installed on?"
date: 2011-06-14
forum: General Help
---

### Post by Shieldmaster on 2011-06-14
Hello,
     I have been using ubuntu for over a month and I installed it on my harddrive's 70gb partition as a 25gb filesystem. Im wondering if I can mount the other 45gb and read that in ubuntu, as of now I can't find a way to do that. Can someone explain to me how to do this if it is possible.

Thanks in advanced

---

### Post by jerrrys on 2011-06-14
are you trying to access windows?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=read+write+ntfs&as_qdr=all&sa=Google+Search&lang=en#986](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=read+write+ntfs&as_qdr=all&sa=Google+Search&lang=en#986)

---

### Post by Shieldmaster on 2011-06-14
No I'm asking how I can read the files on the other 45Gb of my 70gb partition in ubuntu since i installed ubuntu on the same partition 

thanks

---

### Post by hal8000 on 2011-06-14
Can you open a terminal and post output of:

sudo fdisk -l

df -Th

---

### Post by jerrrys on 2011-06-14
ok, lets try again...

format the extra 45G to ext4 and you can read and write to it

---

### Post by Shieldmaster on 2011-06-14
In response to hal800

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x983f7c98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6          18      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              18        9957    79828992    7  HPFS/NTFS
/dev/sda4            9957       19458    76316672    f  W95 Ext'd (LBA)
/dev/sda5            9957       19458    76315648    7  HPFS/NTFS



Jerrrys I would do that but I would have nothing to back up the things on the 45gb part of the partition

Thanks

---

### Post by hal8000 on 2011-06-14
You didn't post


df -Th

You must have done a wubi install as the only thing I see is NTFS partitions. The df will also show sizes, but the answer is first back up all
your data then either create a new partition, or resize/expand the existing
partition.

---

### Post by Shieldmaster on 2011-06-14
Ok thanks both of you ill look for something to backup my files on

---

