---
title: "Filesystem is still there but..."
date: 2011-05-02
forum: General Help
---

### Post by neutro on 2011-05-02
In Maverick, I installed an internal 2TB hard drive on my computer and formatted it using the Disk Utility (Palimpsest). For some reason, I was able to make an ext4 filesystem without partitioning the drive, so I just did that. (This is not the system drive of course, only a secondary drive to store pictures, music and backups).

So I have this 2TB ext4 filesystem laid down on an unpartitioned drive, without a partition table.

Under Maverick, I was able to mount the filesystem and use it without any problem (instead of mounting /dev/sda1 on a mount point for example, I mounted /dev/sda). In fact this was done automatically and I never bothered with mount points, but this is what happened internally I guess.

Now I upgraded to Natty, and I get a disk error message at bootup. The only way pas it is to skip mounting the 2TB disk. I just can't access it at all. I can't mount it using mount, gparted lists it all as unallocated space. The thing is, fsck sees the filesystem and says it alright.

So, what's hapening here? Is it Natty's new kernel or udev that can't see filesystems on unpartitioned disk space? Should I use an older Ubuntu live CD to mount the drive, copy the content elsewhere, then make a partition on the drive and recopy the content on it? It seems a waste of time since the data is still there and seems fine.

Thanks for any hint!

---

