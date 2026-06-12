---
title: "Partition Matter - Move Home folder to another mount."
date: 2010-02-27
forum: General Help
---

### Post by sgiouldasis on 2010-02-27
Hello to all,

I recently installed ubuntu on a new HardDisk of 1TB capacity. I let ubuntu make all the necessary partitions and blah blah, i installed and they booted perfectly.

I'm using them for about a month now and I realised that I need to partition that 1TB HD so I can have it as a seperate disk, that I can also share inside the network.

I used GParted for you's to see the disk:
[[IMG]http://img163.imageshack.us/img163/263/gparted.png[/IMG]](http://img163.imageshack.us/i/gparted.png/)

So here's the deal:
Ubuntu split the HD to 2 partitions, one for / (root) (50GB) and the rest for the /home (me) user.

I want to get the /home mount to be one with the 50GB Partition together with root, and leave the rest HD free for me to use as just another clean mount.

The thing is that GParted doesn't allow me to resize partition unless I unmount the rest disk. To unmount the disk, /home has to change so that the disk can be unmounted.

Thanks in advance...

---

### Post by sgiouldasis on 2010-02-27
Reply

---

### Post by r-senior on 2010-02-27
Have you tried booting from an Ubuntu live CD and using gparted from the terminal? Another alternative is to make a gparted live CD:

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

It should go without saying that backing up anything you can't afford to lose is a good idea.

If it were me, I'd probably keep the separate /home partition, shrinking it to allow your new partition, rather than combining it with /.

No swap partition?

---

### Post by sgiouldasis on 2010-02-27
Ok, then what should i do in ordrer to have a swap partition keep the /home. Mount on the 50gb partition and lastly create another last partition to have it empty.


Another thing that i thought of, is there anyway i can move the entire ubuntu installation onto another disk and just have this 1TB HD for data use... Is there a relatively easy way?

---

### Post by r-senior on 2010-02-27
So the plan would be to have:

1: /
2: /home
3: /data (or whatever you plan to call it)
4: swap

Which would be fine. These could all be primary partitions. The limit is generally four, after which you need to start using extended partitions. As you already have your /home in an extended partition, it makes sense to create /data in there too.

[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics")

Something like this:

1: /dev/sdb1 / (primary)
2: /dev/sdb2 (extended) -> /dev/sdb5 /home (logical)
3: /dev/sdb2 (extended) -> /dev/sdb6 /data (logical)
4: /dev/sdb3 swap (primary)

So, having backed up (did I mention that ;)), you'd need to launch gparted with your current partitions unmounted, then:

a. Shrink /dev/sdb5 to be the size you would like for /home
b. Create a new swap partition at the end of the drive /dev/sdb3 (~1.5 x RAM, max 2GB)
c. Create a new logical partition /dev/sdb6 in the extended partition

As far as copying data is concerned, have a look at this:

[http://ubuntuforums.org/showthread.php?t=416710]("http://ubuntuforums.org/showthread.php?t=416710")

Bear in mind that if you plan to free up the 1TB drive completely, you'd also need to transfer the Master Boot Record (MBR) to the other drive, or at least recreate it on there.

I'm wondering, in that scenario if you'd just be better doing a clean install on the other drive? Then mount up the 1TB drive and move any data/settings across. When you are happy all is well, reformat/repartition the 1TB drive and mount it as your /data volume?

---

### Post by oldfred on 2010-02-27
I also think a clean install is better. I have converted to that for every new update to Ubuntu but since the system is small I only need 10-20GB for the system. I am currently using about 5GB. With Karmic I moved home to a separate partition but also moved all my data that was in home to a separate partition. My /home now is about 1GB with 3 years of hidden file history and some misc stuff. Most is in my data partition and linked into home so home does not look any different than a standard home.

I have also seen comments where with 1TB drives users like to keep a small (4GB) operating system on the drive -  as just in case I need it and can boot it directly if I have to.

You should be able to backup home or copy it to your other drive. That will preserve just about all your settings. If you have installed a lot of applications you can export than using command line or synaptic and reinstall easily. That recreates your system without much difficulty.

Some info on using a data partition:
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data - older but still useful
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Oldfred's version in comments:
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by sgiouldasis on 2010-02-28
Hi guys, so I made a clean install in the end. The only thing that mattered to me and needed to be moved was the apache websites that I had, so I considered "Ok, take the websites, reinstall, re-copy the websites) that's all I think... Sorry for troubling you about resizing partitions and stuff, it's just that I thought reinstalling would be messy and tried to find an alternative way-out.

Thanks for all!

---

