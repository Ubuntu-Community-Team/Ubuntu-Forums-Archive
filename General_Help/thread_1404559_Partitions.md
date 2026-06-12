---
title: "Partitions"
date: 2010-02-11
forum: General Help
---

### Post by mavillen on 2010-02-11
Hi all,

I'm new to Ubuntu and have installed 9.04, first inside windows and then decided I did not want to keep windows on that machine any more so I formated the windows partition with gparted (?). So far all is well and I can access and use it but I think I'd rather have just one large partition instead. Can I change this in an easy way? I.e. I want to remove the old windows partition (18GB) and make that disk space for the original Ubuntu partition which currrently is only 2 GB.

Any suggestions?

Mats

---

### Post by Anxious Nut on 2010-02-11
you can download [gparted live cd]("http://gparted.sourceforge.net/livecd.php") and from it you can manage all partitions of your hard disk. I think this can be done by two steps:
1- deleting the 18 GB partition
2- resizing the 2GB partition to fit the HDD

---

### Post by Joe Ker1086 on 2010-02-11
Yea, gparted live cd will do it...but you have to delete out the windows so that it is unallocated space...then you may have to move the partition then resize it b/c you will show unallocated space on both sides.. im not sure if you can expand it in both directions in one shot....just BE CAREFUL!!!!!!! when you use the gparted live cd you automatically have full root privlages so it is very easy to wipe out your whole drive.

---

### Post by houseworkshy on 2010-02-11
If you are not experianced and don't have things like work which is hard to replace on your disk it might be easier to simply reinstall from scratch and let the live cd do eveything automatically after chooseing use whole disc.  2gb is smaller than a dvd and most memory sticks.  Complications can arise, all solveable but a pain if one is new, when changeing partitions and their sizes.

---

