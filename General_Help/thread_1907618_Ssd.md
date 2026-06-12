---
title: "Ssd"
date: 2012-01-11
forum: General Help
---

### Post by dracayr on 2012-01-11
Hi,
I'm getting a new laptop with an SSD, so I did some research on how to best set it up. MagicFabs ssd checlist: [https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist) recommends turning off timestamps to minimize the data written to disk (and maximize the life of the ssd). I have two issues with that: 1. as far as I know, make (and maybe other programs?) use timestamps to operate. Does anyone know how make will behave when timestamps are disabled completely? 2. Is the data written because of Timestamps really relevant when SSDs nowadays have a life expectancy of ~60TB? (e.g. 60TB can be written to disk before the disk fails). Also, the checklist explicitely says to create only one partition, and no swap. The no swap part is clear, but why would it influence performance if I made two partitions, provided the second partition is also 4k-aligned? (I'd rather have a seperate /home partition)

dracayr

---

### Post by Bobhuber on 2012-01-11
I compile my own kernel along with FF etc. No problems at all with turning off timestamps. The less you have to write to the drive the better off you are.  Some of the statements in that post don't hold true and are a bit outdated. As long as you have a large enough drive and know how to properly align multiple partitions you can create as many as you want. Most poor people (including me) use a small (60 GB) drive for boot and don't need a second partition  . Also you lose space with every partition you create in order to keep the alignment.Anything that I write to a lot goes on a second drive. Putting your log files in memory ( if you have enough memory) not only prolongs SSD life but speeds things up a bit. [http://wiki.geteasypeasy.com/How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://wiki.geteasypeasy.com/How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive)
You want to leave journaling enabled if you are using the drive for boot. After many hours of reading and experimenting here are  the mount options that work well for me on an ext4 file system.

  noatime,discard,barrier=0,data=ordered

You will find a lot of useful links here >  [http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd](http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd)

---

