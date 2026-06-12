---
title: "Partition size for small disk"
date: 2011-01-19
forum: General Help
---

### Post by maxppp on 2011-01-19
Hi, am installing 10.10 on a 7.5GB hdd.

Can anyone recommend what partition(s) i should create,  (primary/logical)|(size)|(filesystem type)|(mount point).

It has 1gb ram, although that will be upgraded to 2 in the next few days.

Much appreciated!

---

### Post by gordintoronto on 2011-01-19
I suggest a swap partition of 1 GB, and give the rest to / (root) as EXT2, 3 or 4. Both as primary partitions.

Make backup often!  An old HDD like that could fail at any moment.

---

### Post by lithopsian on 2011-01-19
Ext2?  Hard to imagine what possible reason there is to do that.  Try ext3 if you're highly conservative, ext4 in most cases.  Probably ext4 is the best solution in this case because a full disk won't fragment quite as badly.

I wouldn't bother with the swap partition.  You don't have that sort of space to spare.  Stick the whole thing in one partition and install.  Create a small swap file and try not to use it.  You can change it later if you need a bit more or a bit less.  You simply don't have space to install 10.10, have a home directory, and waste 1GB.  Configure compcache and you can probably avoid using any swap at all, especially when you get to 2GB.

You won't be able to hibernate and you'll have to keep a constant eye on disk space.  Maybe you should uninstall as much stuff as possible straight away.  Or maybe pick a distro that doesn't install as much in the first place.

---

