---
title: "Very SLOW file copy speed (disk to disk)"
date: 2010-04-22
forum: General Help
---

### Post by Ebon Lupus on 2010-04-22
I'm using Ubuntu 9.1 (a freshly updated install) and have a 320G  disk (sda) and a 250G disk (sdb) installed. I use the sdb drive to back up a portion of the sda drive, about 82G, at this point.

When I start the copy the speed is around 55M/sec and It tells me the estimated time is about 28 minutes. As the copy progresses the speed creeps down to less than 12M/sec, and the estimated time correspondingly increases... to about 1 hour 45 minutes.

Is this a typical issue in Ubuntu 9.1?
Is there a solution?
Am I doing something wrong?
Is there some mystical powder I should be sprinkling on the Terminal?

Any information will be greatly appreciated.

---

### Post by TitanusEramius on 2010-04-22
Without any sources to backup my claim I can't be 100% sure but since I always have had the same speeds you are describing I don't think it's Ubuntu/Linux's fault. Filetransfer depends on several factors:

Filesize. Anything small (like text-files, pictures and so on) will reduce speed.
Fragmentation. Are you copying to/from a NTFS-formated drive?
The drive itself also depends on several things like speed (5400rpm, 7200rpm & 10000rpm) then offcourse the age of the drive have a say in this. Older drives are much slower than new ones.

One thing you could do is to run a drivetest using hdparm:
[http://www.linuxinsight.com/how_fast_is_your_disk.html](http://www.linuxinsight.com/how_fast_is_your_disk.html)

A small warning though, don't use hdparm with other parameters then the "-t" unless you have read the man for hdparm:
```
man hdparm
```

---

### Post by X1R1 on 2010-04-22
I have also the same problem, but worse. When I put a USB flash drive and start copying something, Its starts at about 55MB/s but after a while, sayyy I copy 2gigs, Speed drops dramatically to 500KB/s, this sucks because I have to be constantly copying files to usb flash drives.

hope someone has a solution for this :D

In windows I can copy full speed and transfer rate is very consistent.

---

### Post by CannibalZerg on 2010-04-22
If your USB disk is NTFS-formatted - there is no solution, except reformating it with FAT32.

---

### Post by TitanusEramius on 2010-04-22
> **CannibalZerg said:**
> If your USB disk is NTFS-formatted - there is no solution, except reformating it with FAT32.
Why do you think that?
All benchmarking between the two filesystems are only showing a 5% advantage towards FAT32 but that will not compensate for the speed missing between 0.5 mb/s and 50-80 mb/s. Besides, NTFS is more stable than FAT & FAT32 so unless formating to EXT3 or EXT4 there simply is no point. A transfer rate of 0.5 mb/s is the same speed USB 1.1 is running at, so chances are that some of the hardware isn't configured right or missing some drivers.
[]("http://www.ntfs.com/ntfs_vs_fat.htm")

---

### Post by peyu on 2010-04-22
Same problem here:

I'm trying to do an image of my disk in an external hard drive with dd tool, it's very very very slow:
After 1/2 hour, 20 Gb have been copied.
After 1 hour, 27 GB
After 2 hours, 40 GB
After 4 hours, 54 GB
After 8 hours, 71 GB
And so on...

It seems to be an exponential law, so for 320 GB, it can last  at least 3 days...

Any idea of what can I do?

Thanks !

---

### Post by sot3 on 2011-03-06
The default block size for dd is non-optimal.  Try something on the order of a megabyte.

To mirror sda to sdb:
dd if=/dev/sda of=/dev/sdb bs=1M

To create an image file of the first partition on sda onto the filesystem of a drive that you've mounted:
dd if=/dev/sda1 of=/media/backup_diskname/myfilename.dd bs=1M

---

### Post by pm3003 on 2012-07-07
Does anyone have a solution for this problem ?

I don't have it when the ntfs discs are NOT automatically mounted at startup.

You have to mount them manually each time at startup, but then the speed is normal. I think the problem might be in ntfs-3g. 

Maybe if you change the mounting options in the startup file (I think fstab but i'm not sure) you can get some results.

---

