---
title: "gparted causes multiple entries in nautilus"
date: 2012-01-24
forum: General Help
---

### Post by cornflake000 on 2012-01-24
This is a a strange one to me...  Every time I start gparted, the partition list shown in nautilus is duplicated until I reboot; I have 2 sets of directories showing.  It doesn't cause any problems, it's just annoying. The first set of entries are not mounted and won't because the partitions are already mounted on the second set of entries.  mtab shows all the correct mounts.

Anyone have this issue?  I can't seem to find any entries on this subject even off the forum.  I've done a general search on the internet and also the gparted forum.  Nothing...

I'm running lynx.

... also logging in and out clears the extra directories.

---

### Post by dcstar on 2012-01-24
> **cornflake000 said:**
> This is a a strange one to me...  Every time I start gparted, the partition list shown in nautilus is duplicated until I reboot; I have 2 sets of directories showing.  It doesn't cause any problems, it's just annoying. The first set of entries are not mounted and won't because the partitions are already mounted on the second set of entries.  mtab shows all the correct mounts.
...........

When gparted starts it rereads the Partition Table using the **partprobe** tool (or some mechanism that does the same thing).

If your system somehow creates duplicate entries when this is done then your system has a problem.

---

### Post by oldfred on 2012-01-24
Nautilus will show duplicates if you mount a partition in /home or /media. I just mount in /mnt like /mnt/data and link folders into /home to avoid the issue.

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

### Post by dcstar on 2012-01-25
> **oldfred said:**
> Nautilus will show duplicates if you mount a partition in /home or /media.


Which is why people should **never, ever** mount things in System controlled folders - as those two listed are.

Pity so many brain-dead HOWTOs around the place either tell them to make this mistake or don't tell them not to do this.

---

### Post by cornflake000 on 2012-01-25
> **dcstar said:**
> 
Pity so many brain-dead HOWTOs around the place either tell them to make this mistake or don't tell them not to do this.

The only mention I have ever heard of not using /media as a mount point are in 2 installation specific instructions I read while using Gentoo.  Outside of that, this is the first I have heard of it in 10 years.  Like you say, most instructions tell you to use it.

> 
... never, ever mount things in System controlled folders "like /media"...


No reflection on dcstar but.... can anyone confirm that this is true?  It's just I've never heard of it and Linux is definitely not new to me.

also... "Duplicate mounts of partitions in Nautilus left panel - use /dev/disk/by-uuid/xxxxx..."  This made no difference for me.

one more edit...

I have mounted only one partition in /media that is not a system mount using fstab.  Everything else is automatically mounted by the system in /media (home, /, swap) or is a default in fstab (fd0); all the sda* and sdb*, floppys, cdroms, are in /media by default.  All of these are duplicated when I start gparted and duplicates disappear when I logout and login.

---

### Post by oldfred on 2012-01-25
I do not think it is straightforward. How is removeable different from temporary?

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
> /media/ Mount points for removable media such as CD-ROMs (appeared in FHS-2.3).
/mnt/     Temporarily mounted filesystems.But old links:
[http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSEMEDIAMOUNTPOINT](http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSEMEDIAMOUNTPOINT)

> /media : Mount point for removeable media
This directory contains subdirectories which are used as mount points for removeable media such as floppy disks, cdroms and zip disks.
Historically there have been a number of other different places used to mount removeable media such as /cdrom, /mnt or /mnt/cdrom. Placing the mount points for all removeable media directly in the root directory would potentially result in a large number of extra directories in /. Although the use of subdirectories in /mnt as a mount point has recently been common, it conflicts with a much older tradition of using /mnt directly as a temporary mount point.

/mnt : Mount point for a temporarily mounted filesystem


---

### Post by cornflake000 on 2012-01-25
> **oldfred said:**
> I do not think it is straightforward. How is removeable different from temporary?

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
But old links:
[http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSEMEDIAMOUNTPOINT](http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSEMEDIAMOUNTPOINT)

So it seems we are talking about tradition and continuity rather than conflicts or absolutes which is what I have always thought; you can theoretically mount anything wherever you wish.  

This seems to give the notion that one would consider using / to mount non-removable or non-temporary partitions that I wish to name and mount.  All "left overs" are thrown into media by default.  For instance sda* and sdb* that are not specified in fstab are in /media without my input.  They are neither temporary nor removable.  I would suppose the system considers them to be "temporary".

---

