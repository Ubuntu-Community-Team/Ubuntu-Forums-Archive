---
title: "Partitionphobia"
date: 2012-04-30
forum: General Help
---

### Post by Lloydb39 on 2012-04-30
I have a 1 TB drive, all in one partition. (Ubuntu 11.10 just kind of installed itself that way)  I would like to have the OS in one partition and files in another, I think. But when I started up the partition manager it scared the hell out of me. I have no idea what all those terms mean and I don't really want to wipe out everything on my disk by mistake. Is there any Partitioning for Dummies info that I can turn to?

---

### Post by mendhak on 2012-04-30
I had the same phobia when I started!  I followed this (now out of date but it will give you an idea of what to do) tutorial:

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by oldfred on 2012-04-30
Some guides with screenshots:

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

If you have separate /home or other data partitions, then you / (root) or system partition does not have to be very large at all. I install to 25GB root partitions with about 7GB used. With my 650GB drive and a couple of 100GB data partitions, I now have lots of system partitions.

---

