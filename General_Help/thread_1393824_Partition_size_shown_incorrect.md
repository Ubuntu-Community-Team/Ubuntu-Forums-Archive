---
title: "Partition size shown incorrect"
date: 2010-01-29
forum: General Help
---

### Post by Thomas Garman on 2010-01-29
I have googled and looked around on the forums but I couldn't find anything that directly answers my question.

I have a dual boot set up with Vista and Ubuntu 9.10.  My hard drive is partitioned into dev/sda1 (where Vista resides) and dev/sda2 (where Ubuntu resides) and /dev/sda4 which I use as a shared hard drive for the two operating systems.

When I first installed Ubuntu on dev/sda2 I used gparted to make /dev/sda2 a 10 GB partition becuase I wanted to try putting ubuntu on a very small partition.  Since then I used gparted to expand /dev/sda2 to 32GB.  But when I use System Monitor (System--->Adminstrative----->System Monitor) it shows only that the /dev/sda2 space is 10GB (and says that there are only 2.9 GB) remaining unused.  Yet when I use gparted to look at the partitions, it says that /dev/sda22 is 32 GB with 3.9 GB remaining unused.

I am wondering if anyone knows why they show two different sizes and what I can do to fix the size being shown.  When I tried to make a tar gz back up of my system iit returned a message warning me that my /dev/sda2 partition was almost full because it put the 1.5 GB tar gz file in my home drive (which I suppose the system monitor only sees as a 10 GB space that already has 7 GB in it).

Totally mystified by this.

---

### Post by dcstar on 2010-01-30
> **Thomas Garman said:**
> I have googled and looked around on the forums but I couldn't find anything that directly answers my question.
..........

[http://ubuntuforums.org/showthread.php?t=1242394&highlight=partition+size+incorrect+gparted](http://ubuntuforums.org/showthread.php?t=1242394&highlight=partition+size+incorrect+gparted)

---

