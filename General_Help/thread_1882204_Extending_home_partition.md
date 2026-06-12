---
title: "Extending /home partition"
date: 2011-11-16
forum: General Help
---

### Post by murdockpt on 2011-11-16
I booted into partition magic from usb.

sat for an hour shrinking my windows partition, moving some preexisting partitions and extending the /home partition.

everything looks good, boot into ubuntu, get warning saying ubuntu has less than a gig of space (extended the partition by 30gb to avoid this). check gparted, partitions are correct size.

what do i have to do in ubuntu to extend the partition? tried installing something larger than a gig to see if its just a bug, but the program says theres not enough space, so the OS just says "NO. not enough space!"

grr

solutions? a little drunk but open minded.

---

### Post by oldfred on 2011-11-17
Post these:

sudo fdisk -lu

df -Th | sort

How large is / (root) partition? Minimum is now 4.4GB and we often suggest 10 to 20GB, when you have separate /home or data in a shared NTFS or Linux data partition.

---

### Post by murdockpt on 2011-11-17
i believe i made my /root 15gb

michael@michael-N80Vb:~$ sudo fdisk -lu
[sudo] password for michael: 

Disk /dev/mmcblk0: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e0ef5

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *        8192     7744511     3868160    b  W95 FAT32

Disk /dev/sda: 250.1 GB, 250059350016 bytes
4 heads, 44 sectors/track, 2774983 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    22523118    11261528    c  W95 FAT32 (LBA)
/dev/sda2   *    22523130   199602175    88539523    7  HPFS/NTFS/exFAT
/dev/sda3       199602176   486541311   143469568    f  W95 Ext'd (LBA)
/dev/sda4       486541312   487028735      243712   83  Linux
/dev/sda5       199604224   314941439    57668608    7  HPFS/NTFS/exFAT
/dev/sda6       314943488   344238079    14647296   83  Linux
/dev/sda7       344240128   473845759    64802816   83  Linux
/dev/sda8       473847808   486541311     6346752   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073856

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953458175   976728064    7  HPFS/NTFS/exFAT



michael@michael-N80Vb:~$ df -Th | sort
/dev/mmcblk0p1
/dev/sda4     ext4    231M   55M  164M  26% /boot
/dev/sda5  fuseblk     55G   39G   17G  71% /media/Media
/dev/sda6     ext4     14G  4.2G  8.9G  32% /
/dev/sda7     ext4     30G   28G  754M  98% /home
/dev/sdb1  fuseblk    932G  112G  821G  12% /media/Space
Filesystem    Type    Size  Used Avail Use% Mounted on
none         tmpfs    2.0G  5.0M  2.0G   1% /run/shm
none         tmpfs    5.0M     0  5.0M   0% /run/lock
tmpfs        tmpfs    806M  1.1M  804M   1% /run
udev      devtmpfs    2.0G  4.0K  2.0G   1% /dev
              vfat    3.7G  3.7G  5.4M 100% /media/READYBOOST
michael@michael-N80Vb:~$ ^C
michael@michael-N80Vb:~$

---

### Post by oldfred on 2011-11-17
It looks like you have 28GB in your /home which looks like it is sda7. Normally /home is your data as the system settings are less than one GB. With another 1TB drive can you not move or save your data elsewhere?

---

### Post by murdockpt on 2011-11-17
i would if wine didnt need to save its programs to its own wee little folder.

its weird though that everything else says the /home partition is 62 gb, but ubuntu itself says it hasnt changed.

---

### Post by oldfred on 2011-11-17
Wine is difficult to move as I understand it, so it is the only larger thing I have in my /home, but my /home is between 1 and 2GB with at least 3/4s of that the .wine folder.

Depending on what you use to check sizes, it may include other mounted folders or may not include hidden (.) folders unless you first turn on show hidden folders.

In /home you can check for larger files.

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h

---

