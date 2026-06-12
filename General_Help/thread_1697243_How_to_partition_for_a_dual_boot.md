---
title: "How to partition for a dual boot?"
date: 2011-02-28
forum: General Help
---

### Post by Rockcarver on 2011-02-28
[SIZE=3][COLOR=Green]Ran Karmic for a while in a wubi installation with XP. Very unstable, lots of headaches at inopportune times. Now I'd like to try separate partitions so Windows might leave Ubuntu alone and not nibble it away as it did under the wubi installation.

Here is my current partition status:[/COLOR][/SIZE] 

[SIZE=2]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
129 heads, 4 sectors/track, 605778 cylinders
Units = cylinders of 516 * 512 = 264192 bytes
[/SIZE][SIZE=2]Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4592a56d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      198450    51200098    7  HPFS/NTFS
/dev/sda2          198451      605776   105090108    f  W95 Ext'd (LBA)
/dev/sda5          198451      605776   105090106    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

[SIZE=3][COLOR=Green]sdb is an external drive. Suggestions on how to modify the partitioning of sda to run Lucid in one partition and XP in another would be really welcome. The computer is an Asus laptop.[/COLOR][/SIZE][/SIZE][SIZE=3][COLOR=Green] I have not partitioned a disk before.

Thanks in advance,

Rockcarver
[/COLOR][/SIZE]

---

### Post by spiky001 on 2011-02-28
Have a look here [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

---

### Post by sikander3786 on 2011-02-28
Ubuntu doesn't need a primary partition to boot from and can be installed to a logical one.

What does sda5 contain? If some personal data that you can backup to some other place, it would be better to just delete the extended partition and create 3 new partitions in the freed up space.

1. Data partition, Primary, NTFS, size = custom
2. Ubuntu '/' partition, extended/logical, ext4, size = at least 8 GB. '/' partition holds the base install plus your /home directory if a separate one is not configured.
3. Swap partition, extended/logical, size = at least equal to your RAM.

For an overview of Ubuntu partition, you can follow this link.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

Once you've an idea of partitions, it would be easy to answer your queries. Just post them :-)

---

### Post by Rockcarver on 2011-03-01
Spikey, Sikander, thanks! I'll take a bit of time and read up from those links, and get back with the inevitable further questions :D

---

