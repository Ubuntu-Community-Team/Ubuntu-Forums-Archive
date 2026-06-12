---
title: "Is it possible to mount partitions in spite of fsck errors?"
date: 2010-04-24
forum: General Help
---

### Post by GeoMX on 2010-04-24
I first described my problem here: [http://ubuntuforums.org/showthread.php?t=1455789](http://ubuntuforums.org/showthread.php?t=1455789)

To sum up:

> 
We have a read-only Linux system (I've set it up following these instructions: [http://www.logicsupply.com/blog/2009...-linux-system/](http://www.logicsupply.com/blog/2009...-linux-system/)), we have one disk with four partitions, one for all system files (/), a swap partition and two extra partitions for configuration media files.

The /etc/fstab contains only the last two partitions and I'm using UUID for referring the devices.

The problem I'm facing is, when testing the system with one motherboard, everything works perfect, both extra partitions are mounted at boot time. But when using another motherboard (same model than the previous), the extra partitions do not mount at boot, they can be mounted manually running mount command, but have no clue why they can't be mounted at boot. For a SATA disk, only one extra partitions is mounted at boot, testing with an IDE, both partions are not mounted.


The problem was that fsck returned an error regarding the difference between internal date/time and last time the disk was mounted. Adjusting motherboard's date/time fixed the problem and so I marked the thread as solved. However, I find the problem again with every new motherboard I try, and before adding a manual mount script (mount -a) to the system I'd like to know if there is a way to receive these messages but also get the partitions mounted.

Thanks in advance for all of your help.

---

