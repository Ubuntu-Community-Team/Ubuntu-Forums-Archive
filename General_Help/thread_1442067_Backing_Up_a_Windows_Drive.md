---
title: "Backing Up a Windows Drive"
date: 2010-03-29
forum: General Help
---

### Post by Imamoomoocow on 2010-03-29
Hello =)
I run a three hard drive system, one disk is ubuntu, one is windows 7, and the last is a general ntfs storage drive that i use to send files between my two OS's. What I want to do is backup my entire windows 7 disk (maybe image it?) so that in the event it breaks, I can restore it on a new drive without losing my setup. 
I already did a "cp -a" copy of the entire disk, but i don't think I can restore from that and still have the drive bootable (right?)

Do you guys/gals know the best way to achieve a full backup of an entire drive (two windows 7 partitions)?
Thanks for reading :D

---

### Post by srs5694 on 2010-03-29
You can back up the individual NTFS partitions with ntfsclone. Read its man page for details. Restoring the system to bootability can be tricky, though; Windows is very fussy about its boot partition, and it will refuse to boot if you restore to anything other than the original starting sector. You can do this if you have sufficient partitioning information, such as the output of "fdisk -lu", but you'll need to know what you're doing when restore time comes around.

Alternatively, you could look into [Clonezilla,](http://www.clonezilla.org/) which is designed for easy whole-disk cloning. I've never used it myself, so I'm not sure of its precise features, but at the very least, it should help automate some of this process. I don't know if it has any means of overcoming Windows' sensitivity to the start sector of its boot partition.

---

