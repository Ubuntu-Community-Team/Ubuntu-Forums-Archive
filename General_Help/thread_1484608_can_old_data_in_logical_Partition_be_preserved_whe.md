---
title: "can old data in logical Partition be preserved when new install unbuntu?"
date: 2010-05-15
forum: General Help
---

### Post by GoldyW on 2010-05-15
I want to install Ubutn-Server-9.04 on a disk.

This old windows-used disk has three patitions:
   1 # -- Primary NTFS
   2 # -- Logical  NTFS
   3 # -- Logical  FTA32

I plan to install Ubuntu on 1# Partition and override the old OS-Windows7.

but the Data on 2# and 3# partition can still be preserved?

---

### Post by GoldyW on 2010-05-15
on-line waiting...

---

### Post by srs5694 on 2010-05-16
Yes, you can preserve those partitions. I'd recommend using the "manual" or "advanced" partitioning option during installation. (I don't recall which term is used.) You can then select partition #1, delete it, and create your Linux partitions there. I recommend creating three partitions:


[list]
[*]**root (/)** -- The bulk of the Linux installation goes here. Make it about 5-20GB, depending on how much space you've got and how much software you plan to install. Set its mount point to "/" (pronounced "root").
[*]**swap** -- This partition is used for suspend-to-disk operations and when Linux needs more memory than you've got installed. It should be 1-2 times the size of your RAM. It doesn't have a mount point.
[*]**/home** -- This partition will hold all your personal files. Give all the space you haven't given to the first two partitions to this one. Its mount point is "/home". (If the partition you're deleting is smaller than about 30GB, you might want to omit this partition or shrink and move your existing partitions to make more room for /home. Be aware that shrinking/moving existing partitions is a bit risky -- a power failure or system crash can destroy the partition. Back up first, if possible.)
[/list]


In theory, all of these can be logical partitions. In practice, I'm not sure what the Ubuntu installer will permit on this score, given your existing layout.

You can also give mount points to your existing partitions, which will make them available at particular locations in your directory tree. For instance, if your username will be "goldy", you could mount your existing partitions at /home/goldy/ntfs and /home/goldy/fat, to make those partitions available in the "ntfs" and "fat" folders within your home directory.

---

