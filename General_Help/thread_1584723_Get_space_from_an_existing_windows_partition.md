---
title: "Get space from an existing windows partition"
date: 2010-09-29
forum: General Help
---

### Post by cyrus_nk on 2010-09-29
Hi guys!

My current setup is a dual boot Ubuntu 10.4 and Windows XP(one partition for the system and one for general use, let's say E: drive).

How can i get some disk space from the general use E: drive and grow the /home Ubuntu partition? What is the "safest" way?

I'm not very experienced with Linux and the terminal but i'm willing to learn. :P

Thank you.

---

### Post by oldfred on 2010-09-29
Anytime you repartition you should have good backups. There is always a risk of corruption. Is /home within root or a separate partition or a partition you want to make?

You should be able to do what you want with gparted from a liveCD. You cannot edit partitions that are mounted. From the liveCD sometimes you also have to use swapoff as it mounts the swap partition automatically.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Expanding/Resize an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Windows and NTFS partitions require 20-30% free space to work well so be sure not to shrink too much.

---

### Post by 7h3d4rk0n3 on 2010-09-29
Typically, it is safer to shrink a Windows partition from within the Windows operating system. XP, however, does not have this feature built in. So, in this case you could probably use GParted. Just be sure to back anything up that you do not want to lose (copying it to your Linux partition would be an efficient way to do so).

---

### Post by cyrus_nk on 2010-10-02
Hi guys and thanks for the reply.

I'll try. Maybe in a few months i'll shrink the xp partition to zero :))

Have fun!

---

