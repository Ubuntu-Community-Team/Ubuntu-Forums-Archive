---
title: "Large transfer to Universal Disk Format device breaks"
date: 2011-04-30
forum: General Help
---

### Post by luigi6699 on 2011-04-30
I have a big video archive, which I am trying to copy to it's own terabyte USB drive.  The drive is one that I use on Ubuntu, OSX 10.6, and occasionally Windows 7... so it looks like my best bets as far as file format are FAT32 and UDF.  I've been trying to do it with UDF, and everything seems to work... but copying the actual data over fails.

I formatted the disk in two steps - OSX is a BSD variant, and it has a hard time with UDF devices originally created under other systems.  So I did this from OSX:

```


$ dd if=/dev/zero of=/dev/sdX bs=512 count=1  #gotta zero the boot sector, cause UDF doesn't use it and having a boot sector that says "FAT" can confuse...

$ newfs_udf /dev/disk1
```

Worked like a charm.  I can copy and read files between Ubuntu and OSX.  So I attached the drive to my Ubuntu 9.11 machine, and tried copying everything over with rsync:

```
$ rsync -r -vv /media/TIGABYTE/VIDEO /media/disk > ~/rsync-video.log

```

Everything seemed to work well, so I left it copying for awhile.  When I came back, there was nothing unusual in the log file... except that it had mysteriously stopped after 67 movies.  I have 365 movies in that folder!  On further inspection, rsync had died complaining that there was not enough free space (that's why I'm moving files off there in the first place!.  The source drive has no free space, but the destination drive has literally hundreds of gigs to spare.  Just to make sure I was sane, I tried rsyncing just a couple of big files, and got no errors.

According to the rsync docs, it shouldn't require any space on the source device... but just in case, I thought I would try this with old fashioned cp. 

```
$ cp -Rv /media/TIGABYTE/VIDEO/ /media/disk/ > ~/cp-files-transfer.log 
```

This also seemed to work fine, until I came back and discovered even weirder discrepancies.  The logfile I created has the right number of lines in it, and there are no errors recorded.  df tells me that 459M is used on the device, which is about right.  But if I try to do anything with the device, it just hangs.  touch, ls, everything just hangs.  Ps tells me they're in foreground uninterruptible sleep (D+), and of course they don't respond to kill -9.  

If I plug the drive into my OSX machine, I can see (and access) 56 movies.  OSX thinks there are 999GB free, which is definitely not accurate.

I have no idea what is going on here.  There doesn't seem to be an equivalent to fsck.udf out there, so I can't just check the drive's integrity.  I'm starting to think this may be an issue with BSD/Ubuntu compatibility on the UDF format.  Any ideas?

---

### Post by Paddy Landau on 2011-04-30
Looking around Google, I believe that UDF is not well supported in Linux.

You can try to install [libudf0]("apt:libudf0"). Reformat your drive and check whether it then works properly.

Can OSX read and write NTFS? If so, that would be your best bet. Ensure that you have [ntfs-3g]("apt:ntfs-3g") installed (it should already be).

---

### Post by luigi6699 on 2011-05-01
Hm, kernel 2.6.30+ is supposed to have full UDF support built in.

Since I made this post, I tried attaching the two disks to my Mac to run the same rsync command.  IT ran, and re-copied every file.  This despite the fact that there were so many already in there!  I've since verified this by doing an rsync within the UDF drive: rsync has some trouble reading the timestamp on the old FAT32 device.  After some googling that's not entirely unprecedented.  So that could be what's causing at least part of the problem on Linux.

I've considered working with NTFS... but FUSE drivers run in userspace, and have terrible performance. Not to mention I hate the thought of using a proprietary Microsoft disk format for sharing data between a Linux and a BSD machine.

Very frustrated that we don't have a real cross platform file format. 

What about ext2?

---

### Post by Paddy Landau on 2011-05-01
> **luigi6699 said:**
> What about ext2?
Although Windows drivers exist for ext2 and ext3, you may find some problems with that. I have not found performance problems with NTFS.

If you want to be cross-platform, you always have to go with the lowest common denominator -- in this case, Windows, using either FAT32 or NTFS. The latter choice is more reliable.

---

