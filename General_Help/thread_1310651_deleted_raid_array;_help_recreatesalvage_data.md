---
title: "deleted raid array; help recreate/salvage data?"
date: 2009-11-02
forum: General Help
---

### Post by Tuna13 on 2009-11-02
Hello,

I'm having some issues with my raid array, and was hoping someone could help me figure out how to safely mount it.

I was using a two disk Raid 1 array when my sda died. I replaced the defective hard drive and simultaneously installed ubuntu 9.10, out of convenience. Problem was, while I was deleting and recreating raid arrays (md0,md1,etc...) I accidentally deleted md5 which houses important data. :(

md5 contains sda4 and sda5. In ubuntu using **cat /proc/mdstat** i have successfully determined that sda4 has resynced and copied all of sdb4's data successfully.

How can I recreate md5 without destroying the data in sda4 and sdb5? My knowledge of linux is mute so precise instructions would be appreciated!

My computer partitions in case someone needs:

md0: contains sdb1 (sdb1 not added yet); swap partition
md1: sdb2 and sda2; empty
md2; sda5 and sdb5; ubuntu 9.10 boot partition
md3; sda6 and sdb6; empty
md4; sda7 and sdb7; empty
md5; sda1 and sdb1; no file system in raid array but individual partitions on drives have files and ext3 file system

I created the raid arrays through the alternative installation cd.

Any help or any info at all is greatly appreciated. Thank you! :D

---

