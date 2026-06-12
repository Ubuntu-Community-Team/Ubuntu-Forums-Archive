---
title: "_Partition Tools in Ubuntu"
date: 2010-01-23
forum: General Help
---

### Post by ic2 on 2010-01-23
Do Ubuntu have a build in partitioning application.  What is the name this application and where is it located?

Also is it possible to create or resize other (out-side) partitions from my Ubuntu partition?  I have a 1000GB drive and Ubunta now has the first 100GB.  I want to work with the other 900GB of disk space useing the partiton tool from WITH-IN Ubuntu while running, if possible.

What is the name of this tool and where is it. Are there more than one partitioning tools inside the latest version of Ubuntu?  Hope I explained this fairly well.

Thank in advance

---

### Post by pastalavista on 2010-01-23
Gparted is included on the live CD but not installed by default. After you install it ```
sudo apt-get install gparted
``` you'll find it in the System--> Administration menu. If you need to change your root (/) partition, you'd have to use the live CD anyway because you can't change a mounted partition..

---

### Post by nmaster on 2010-01-23
there is also a seperate gParted liveCD.  i think it has more features than the version on the ubunut liveCD.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by louieb on 2010-01-23
> ? ... build in partitioning application.  
Gparted, fdisk, cfdisk, sfdisk, parted, testdisk and there other available. 

> Also is it possible to create or resize other (out-side) partitions from my Ubuntu partition?

Yes, all the tools will work on partitions **out-side** the Ubuntu install partition.  

For someone new to partitions and partitioning Gparted is my recommended application. Its the only one I listed with built in sanity checks and the only one with a GUI. 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 

> Are there more than one partitioning tool
The others I named are command-line tools. Hacker tools - used correctly can fix a broken partition table. Used incorrectly can mess things up so bad - all that left is to start over.
i.e. [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

---

### Post by ic2 on 2010-01-23
Wow! This is why I think Ubuntu is going to Win out and be the most popular Linux distro, if not already.  What a great OS and forum.  One more  thing.  Is LVM a actual partitioning tool and do it comes with the new Ubuntu on CD.  Are there any pros and cons to using it.  If it is one I got a feeling it's like what louieb said about the other he listed.

Thanks everybody

PS: If my font appear too large please let me know so I can make final ajustment.  There was a problem once before when I first join the fourm.

---

### Post by ic2 on 2010-01-23
Disk Druid should work for Ubuntu too.  Thanks again for all the possibility :)

---

