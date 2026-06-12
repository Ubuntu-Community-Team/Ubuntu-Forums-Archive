---
title: "Cant access partition"
date: 2010-07-12
forum: General Help
---

### Post by Howy on 2010-07-12
So, when i installed Ubuntu i made 3 partitions for use: a 253Gb one for documents, another in same size for system and a 490Gb for some other stuff.
However, i cant access the 253Gb one, the rights of it is set to root. :mad:
It was made like that when i installed it, and i dont have a clue why.
How can i make the rights for this partition mine?
Id really like to use it.

---

### Post by Zip247 on 2010-07-12
Can you post the output of 

```
sudo fdisk -l
```

that is a lower case l not a one.

---

### Post by Howy on 2010-07-13
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000599b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30728   246814323+  83  Linux
/dev/sda2           30728      121602   729946113    5  Extended
/dev/sda5           60801      120994   483497984    7  HPFS/NTFS
/dev/sda6          120994      121602     4881408   82  Linux swap / Solaris
/dev/sda7   *       30728       59577   231734272   83  Linux
/dev/sda8           59577       60801     9825280   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23471   188530776    7  HPFS/NTFS
/dev/sdb2           23473       24321     6819592+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)

```
Note that its the first one, sda, that i am having trouble with.
Some other things i have noticed is that there is 7Mb of unallocated space, its just some small parts in between the partitions.
Dont know how that happened.
It doesnt matter if the partition i want to have as storage, is the first partition?
And it is possible to have it as ext4? Or is that an issue?
The 2 other are other things. (sdb is a Windows XP installation from my previous machine. Just for some old files.)

---

### Post by Morbius1 on 2010-07-13
Can you post your fstab because I still don't know what partition is giving you the problem:
```
cat /etc/fstab
```

---

### Post by Howy on 2010-07-13
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=05042069-be03-441a-adaf-07c61f0f579b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c6874d5e-24fe-4d38-b45c-c3cc131fa556 none            swap    sw              0       0

```

Arent there any commands i can do to change the ownership?

NVM, found out how to change ownership, its as simple as this command:
```

sudo chown (username) (path)

```
I have been thinking of using this partition for storing my documents. Would it be risky if i moved the user-folder in /home to this partition and then symlink it back there?

---

