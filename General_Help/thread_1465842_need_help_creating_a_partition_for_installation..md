---
title: "need help creating a partition for installation."
date: 2010-04-29
forum: General Help
---

### Post by hedgeberg on 2010-04-29
To install ubuntu 10.04, I've tried to create partitions on my hard drive, and an external hard drive. Both have failed. I have apparently exceeded the max number of partitions on my hard drive (came with 4 on it. Recovery, OS, and 2 others I don't want to mess with.), and the external hard drive won't let me shrink the NTFS volume to create space for a new partition. Can I get steps to create a new partition, preferably on the external drive (it has more space). My computer is a dell inspiron 1525 with a 225 Gb hard drive, And my external drive is a windows system Seagate 1 Tb Hard drive (I've checked, external drive works with ubuntu).

---

### Post by BrianIsNew on 2010-04-29
I'm assuming you have a functioning OS on your laptop already. Is it Windows? If so, why not try **connecting your external drive**,** right-clicking My Computer**, **clicking Manage**, then find **Disk Management**. Use that to fandangle your partitions.

You may want to do a little reading on [disk partitioning]("http://en.wikipedia.org/wiki/Disk_partitioning") before you begin, though.

---

### Post by hedgeberg on 2010-04-29
thats what ive been doing. Just accessing through control panel instead. And i did my research along time ago. Im only just now getting back up on the ubuntu horse.

---

### Post by BrianIsNew on 2010-04-29
Awesome. I think partitioning is a beast in itself. There's as many ways to "properly" do it as there are "improperly". Just gotta find what makes sense to you.

Was there still a question in there, though?

---

### Post by oldfred on 2010-04-29
Lots of info if you want:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by hedgeberg on 2010-05-01
My problem doesn't seem to be mentioned. I have 2 things I can try. 
1. I made a Gparted live disk, and I can't boot from it. what can I try to make this work?
2. I can try to unmount the hard drive's partition, which may allow me to shrink it. how can i do that in windows?

---

### Post by oldfred on 2010-05-01
I did not see what version of windows. XP does not have partitioning tools. Vista & 7 have the MMC see post #2 that you run from their disks.

Did you make a bootable CD for gparted or copy the ISO to the CD?

---

### Post by hedgeberg on 2010-05-02
using vista. I've been using the built in partition manager mentioned before at this point. and I made a bootable disk of gparted using Roxio. When I try to load the disk at startup, it shows something similar to a terminal window. Loooooong lines of commands. After a while it just stops adding lines. I think my computer needs something to load the disk. Do I need to install ubuntu to use the disk?

---

### Post by mykulz1 on 2010-05-02
Can you not use gparted on the ubuntu live cd instead then?

---

### Post by hedgeberg on 2010-05-02
wait, the ubuntu live cd uses gparted? Didn't know that option was available. I'll give that a try. Thanks. If it works, ill set this as solved.

---

### Post by hedgeberg on 2010-05-03
ok, got the live cd for 10.04 functional. next problem: I have built a partition on my external hard drive (NTFS, named U:, for ubuntu), and when I run the installation program I cannot access the hard drive to install to unless I open manually choose partitions, and I have no idea how to work this mode. How can i choose a partition already functional in the choose manually mode of installation, to install to.

---

### Post by oldfred on 2010-05-03
That is what manual mode is. You choose the partitions your want to use. Besides / (root), you need swap and should also have /home partitions set up in advance. If an existing /home you do not select format. You click on the partition and right click to choose what the partition is and what format ext3 or ext4 to make it.

---

### Post by hedgeberg on 2010-05-04
so, what size should I make each partition, and can I put them all in an extended partition? I assume the root system needs to be the largest, but I have no idea about the other 2. Also, I only learned about ext3 and ext4 partitions as of recently. I have no idea what the advantages are. As you can see, I'm something of an Ubuntu Noob. If you could, just help me with a short explanation.

---

### Post by oldfred on 2010-05-04
All linux or data partitions can be logical in the extended partition. Its windows that has to boot from a primary. Second installs of windows can be a logical also but will not boot without the first install in a primary.

With Karmic I converted from just root & swap with some shared data with XP in a NTFS partition that both could easily read.

When I converted I moved /home into a 100GB partition and now my root is only 5-6GB with lots of programs installed. I then moved all my data out of /home and now /home is only 1-2GB (still in that 100GB for now). All my data is now in another partition most of another 100GB is 75% used. So the real question is how much data do you have or expect to have until you upgrade to a bigger hard drive? And how much space you now have. Over time you needs will change.

I suggest a root of 10-20GB, swap equal to RAM memory, and the rest /home so it can hold all your data. You can leave some unallocated in the extended partition if you want for additional partitions. I have several extra root partitions of about 20GB, one is old Ubuntu install and another for beta installs just to test.

---

### Post by hedgeberg on 2010-05-06
I have a 1 tb external hard drive, and I'm giving myself 150 gig partition to start. Just to get started. The 150 gigs is all one big external partition. So, I need one /home partition, one /root partition, and one "swap parition" (what does this mean?). Are there any other specifics you need to know?

---

### Post by oldfred on 2010-05-06
Swap is if you use more memory than RAM. With more than 2GB of RAM you have to work pretty hard to use swap like edit videos or load every program you have. Swap is also used for hibernation, copies RAM to hard disk, so swap should be as least as large as RAM.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

If creating /home you have to use manual partitioning:
Install karmic Screens shown with advanced button Lucid similar
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by hedgeberg on 2010-05-06
Got everything, I think. Last question: will I need to install the boot loader on my laptop since I'm installing to a USB hard drive?

---

### Post by oldfred on 2010-05-07
Screen #8 of the Lucid install at "Ready to Install" has an advanced button. Click on it and make sure to install grub to sdb or whatever your external drive is.

It is not difficult to reinstall windows or grub boot loaders:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by finlost on 2010-05-07
[This YouTube video gives a good audio and visual description of the various partitions]("http://www.youtube.com/watch?v=40ijcL4YfSc&playnext_from=TL&videos=Ml36pYzxbB8")

---

### Post by hedgeberg on 2010-05-09
ok, everything seems 2 run fine, ubuntu loads well, but I want to edit the grub so that when I can't load from the external hard drive, I load windows from my computer instead. Is this possible? if not, I'm going to have to know how to change the system so that ubuntu doesn't even try to load. This computer belongs to my family, and they need to run windows. I can run windows through the loader, but when the hard drive takes a long time to load it doesn't work. So, how do i set windows to default loading system?

---

### Post by hedgeberg on 2010-05-09
Just need to change it to dual boot mode instead of single boot into ubuntu. How do I change it?

---

### Post by hedgeberg on 2010-05-09
I'll start a new thread for that last question, actually. I've learned what I need to, and I have a functioning ubuntu system. Thanks to all that helped. I'll mark this thread as solved

---

