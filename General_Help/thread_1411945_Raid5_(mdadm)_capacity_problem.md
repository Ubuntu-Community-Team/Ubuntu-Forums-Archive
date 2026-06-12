---
title: "Raid5 (mdadm) capacity problem"
date: 2010-02-20
forum: General Help
---

### Post by TinyKnob on 2010-02-20
I've had a raid5-array consisting of 3 1,5TB disks working in my file-server for several months.  After realizing I needed more space, I got two more disks, and have now removed the old array, and created the new array with 5 disks.

The new array is mounted, shared using Samba, and seems to be working fine.  However, I'm a bit puzzled.

If I type "df -h", the array shows up liks this:
/dev/md0  5,4T(capacity)  187M(used)  5,1T(free)  1%  /mnt/media

Why is there such a big difference between the capacity (5,4T), and the free space (5,1T)?

Also, when I right-click the network-drive on my Windows-PC, and select "Properties", I get these results:
Used space: 279 GB (!?!)
Free space: 5,09 TB
Capacity:   5,37 TB

This can't be correct.

Any help is highly appreciated.

---

### Post by kidders on 2010-02-21
Hi there,

Whether all that's reasonable depends on what filesystem you're using & whether/how you tuned it. For example, supposing it's a default Ext3 filesystem ...[LIST]
[*]The 279GB used (as reported by Windows) may not actually be in use ... it could just be that Windows can't tell the difference between "used" and "not free". It corresponds roughly to the amount of disk space fsck would reserve by default on an Ext filesystem.
[*]Linux, on the other hand, *can* tell the difference between used & "not free", which might account for the 0.3TB difference between total capacity & free space.
[*]The other differences may just be rounding errors ... it's hard to be sure when one set of numbers is accurate to more decimal places than the other.
[/LIST]Can you post the command you used to create the filesystem?

---

### Post by TinyKnob on 2010-02-22
Thanks for replying. :)

To create the file system, I simply used:
```
sudo mke2fs -j /dev/md0
```

In other words an Ext3 file system, if I'm not mistaken.  What other types of suitable file systems are there to choose from if I were to avoid this loss of capacity?

---

### Post by kidders on 2010-02-22
> **TinyKnob said:**
> ```
sudo mke2fs -j /dev/md0
```I'm not sure that's a great idea. Given the size of the filesystem, it's at least worth *considering* making a few usage-specific tweaks. Six months down the line, if you find it's performing poorly, recreating it would be a major headache!

> What other types of suitable file systems are there to choose from if I were to avoid this loss of capacity?Other common filesystem choices include JFS, ReiserFS, Ext2, Ext4, XFS and so on. All have their own unique (dis)advantages.

By the way, reserving filesystem blocks doesn't result in a loss of capacity. On the contrary, it can often *increase* capacity by combatting fragmentation. If you don't want to reserve any of your filesystem, just use **mke2fs -m0** to set the reserved block percentage to zero (see the man page). There's no need to change filesystem type.

---

### Post by TinyKnob on 2010-02-22
Ok, could you give me some specific suggestions on what to do?  The array will for the most part be used for large video files.  This includes single files with sizes around 5-20 GB, backups of DVD-movies, DivX/Xvid files of varying sizes, etc.

I appreciate the help, as I'm totally green when it comes to Linux. :)

Edit: Sorry if I seem to expect to have the answers handed to me, but I'm a bit anxious to get my backed up data from the old array up and running quickly.

---

### Post by kidders on 2010-02-22
> **TinyKnob said:**
> I'm totally green when it comes to Linux.No worries ... There's very little Linux-specific to it, really. The same sorts of issues crop up with all operating systems. Some examples ...[LIST]
[*]You might want to increase the block size, which wastes space, but can improve performance on filesystems containing large files, and help keep a lid on fragmentation.
[*]You should ensure your filesystem block boundaries are aligned to the stripes on the underlying RAID array. This is less important if your hard disks have very big buffers, but in general, mis-aligned stripes can *seriously* hit performance, especially with RAID 5.
[*]Since the files you're storing are so big, you might want to override the default inode count, to reduce the amount of filesystem capacity you throw away on inodes you'll never use. (You may only save a few hundred megabytes though.)
[/LIST]

On software-based arrays, the biggest concern with RAID 5 is write performance. If your array is software-based, any compromise you can make that would have the effect of boosting it would be worth considering. For example, dropping the filesystem journal could dramatically boost write performance, but at the cost of corruption resistance. Possibly unwise!

Since you mentioned alternative filesystem choices earlier, it's worth adding that you might want to spend a few minutes thinking about whether Ext3 is the right choice for you. There are a few practical & performance-related issues with it that are not necessarily shared by other filesystems. One simple example is the (comparatively) colossal amount of time it takes to run fsck on it. Most others are quite a bit faster.

Anyhow, I hope that's of *some* help. Filesystem optimisation is a gigantic field!

---

### Post by TinyKnob on 2010-02-23
Thanks for all your help.  I'll have to look into this subject in more detail eventually.

---

