---
title: "Cross-platform filesystem"
date: 2006-06-19
forum: General Help
---

### Post by dnel83 on 2006-06-19
Hi,
I currently have two large hard disks which I house in a server at home simply providing network access to the software they contain by Samba. These disks are both formatted using ReiserFS 3 and the server is using Ubuntu server. This is a headless box which remains powered pretty much 24/7 for all members of the household to use.

I also have a separate workstation running Dapper and Windows 2000 for some DirectX games which won't function in Wine. I would like to retire the server and merge to two disks into my Workstation in the hope that it will save on power (and the environment :))and fan noise however these discs will need to remain available to the network when I'm running both Windows and Linux, the odd reboot not being an issue. 

I need the hard disks to be both readable and writable in both OS's although as far as I'm aware only FAT32 is supported by both OS's for writing and these disks are far too large for FAT32. There is a reiserFS plugin driver for Windows that I found [here]("http://rfsd.sourceforge.net/") but this appears to be read only. It's would be surprising that there is no read/write filesystem driver which can be shared in both Linux and Windows for large hard disks so is anyone aware on one which I could use?

TIA
dnel

---

### Post by ltmon on 2006-06-19
You are right not to do anything serious with FAT32.  You lose your permissions and captilisation of file names, not to mention the limit on length.

The best solution I think is to use the ext2 drivers for Windows.  As ext2 is fully backwards compatible with ext3 you can format your linux drives as ext3 and access them from Windows with this driver.

There's a couple of implementations.  I couldn't tell you which is best:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

EDIT: Please report back how it works out.  I'm going to do the same when some new hardware arrives.

---

### Post by mips on 2006-06-19
EXT2/3 is supported in windows via the ext2ifs driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Ltools provides some Reiser support, [http://www.it.fht-esslingen.de/~zimmerma/software/ltools/ltools.html](http://www.it.fht-esslingen.de/~zimmerma/software/ltools/ltools.html)
[http://www.it.fht-esslingen.de/~zimmerma/software/ltools.html](http://www.it.fht-esslingen.de/~zimmerma/software/ltools.html)

---

### Post by dnel83 on 2006-06-19
How well does ext2/3 work on large drives (200GB+)?  I can't say I've used it for a long time and tend to prefer more modern filesystems which are designed with large drives in mind.

---

### Post by ltmon on 2006-06-19
I don't think ext3 is as speedy as reiser (especially reiser4) but it should be quite solid.  It is the default on a lot of distributions.

L.

---

### Post by dnel83 on 2006-06-19
[QUOTE=ltmon]I don't think ext3 is as speedy as reiser (especially reiser4) but it should be quite solid.  It is the default on a lot of distributions.

L.[/QUOTE]

Thanks I'll give it a go, has anyone any experience with those two drivers so I can get some idea of their stability/performance?

---

### Post by cotcot on 2006-06-19
I have the driver-fs to read and write from XP to Breezy without any problem. It is on a 160 GB HDD and also to an external 200 GB HDD.

---

### Post by Luke771 on 2006-06-19
There are ext2 drivers for windows?!?
Cool!
I'm going to have some converting to do...

BTW I'm still running Ext2 and never had any problems with that (but my drives are not particularly large: 1x40g and 1x80g).
Never had any problem with FAT32 either, so I don't think I actually need to convert or reformat my partitions with all the back-up-and-restoring work that comes with that... not today at least. The only time I remember having a problem because a file was too big to be written on FAT32 (over 4 gig) was when I tried to extract a X-Plane DVD image file... and when I finally managed to burn the DVD and install the thing, came out that it sucks. But that's another story

Since then, I never needed to write a file bigger that 4gb. (yes, I know the '640k should be enough for anybody' story) and I don't really understand what the problem with capitalization is, but anyway. Cool to know that there are ext2 drivers for windows around. I will think about that next time I have to reformat a partition.

---

