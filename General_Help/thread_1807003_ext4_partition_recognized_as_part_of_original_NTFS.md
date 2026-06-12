---
title: "ext4 partition recognized as part of original NTFS partition in fdisk"
date: 2011-07-18
forum: General Help
---

### Post by VigilanceOfFreedom on 2011-07-18
I just installed ubuntu via the windows executable and I couldn't mount my NTFS partition.  I found this a little odd and I checked fdisk and it seems to think I don't have an ext4 partition as my entire internal HD is displayed as NTFS.  Here's the fdisk output:

[i]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a3eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS[/i]

When i try to mount the NTFS partition /dev/sda2 i get the following output: 
[i]mount: /dev/sda2 already mounted or /media/windows busy
mount: according to mtab, /dev/sda2 is mounted on /host[/i]

I can't make heads or tails out of this.  Anyone know what's going on here?

Edit:

Windows recognizes that 30GB were taken from the NTFS partition for my linux install.  It reads the max partition size as 465GB.  fstab reports the NTFS partition size as 488GB.

---

### Post by oldfred on 2011-07-18
I believe you have installed the wubi version which is just a file inside the NTFS windows partition. It is intended for windows users who want more of a test than the liveCD, can easily uninstall and do not want to repartition since they are not yet sure they want Ubuntu.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by VigilanceOfFreedom on 2011-07-18
Thanks for the fast reply!  That makes so much sense lol.

---

