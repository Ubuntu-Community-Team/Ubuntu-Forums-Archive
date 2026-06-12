---
title: "Unable to mount partition"
date: 2011-02-17
forum: General Help
---

### Post by Rushyang on 2011-02-17
Hey folks!

I just set up a Triple-Boot Machine.. I have 2 HDDs: 160GB+500GB ... Out of which, 160GB is the whole hard-disk, which I used for triple-booting.. and my problem is I am not able even watch one of my most important partition of another HDD ie 500GB.

Here is my fdisk..
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbfd1f177

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11749    94371840    7  HPFS/NTFS
/dev/sda2           11749       46996   283115520    7  HPFS/NTFS
/dev/sda3           46996       60802   110896128    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1b8cea08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9727    78126844    7  HPFS/NTFS
/dev/sdb2            9727       15563    46875000   83  Linux
/dev/sdb3           15563       19458    31288981+  af  HFS / HFS+



Problem which I reckon is, My Mount point of Ubuntu os (From /dev/sdb2) & That /dev/sda2 partitions are shown same in the Gparted Partition manager. Now I just need to know how can I mount this partition?

Screenshots are attached too.

---

### Post by dontbugmee on 2011-02-17
yeah, you need to remove the / mount point from the sda2 partition first, not sure how though, 
probably with the edit function, and don't select any mount point, just dont accidentally format them

mounting it should be easy, just make some folder under /media/ and then

sudo mount -t ntfs-3g /dev/sda2 /media/somefolder/

---

### Post by Rushyang on 2011-02-18
It's solved...!! 

(For the future use, if any ubuntuforums user has the same problem...)

I installed "mountmanager" via Package Management System. (Ubuntu Software Center).. Made directories in the "/media" for each partition through terminal with the help of sudo. Backed Up my old /etc/fstab. Reassigned all mount points to those respected directories & reboot the computer.

---

