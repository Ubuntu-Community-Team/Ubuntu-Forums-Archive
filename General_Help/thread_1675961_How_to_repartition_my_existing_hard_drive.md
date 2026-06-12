---
title: "How to repartition my existing hard drive???"
date: 2011-01-26
forum: General Help
---

### Post by debmalya_92 on 2011-01-26
Hi, i am fairly new to ubuntu. I am using ubuntu 10.10 (maverick meerkat), and i am loving it.
While installing, i hadn't created multiple partitions. But now i feel the need to create a few. How can i repartiton the hard drive without reinstalling??? PLz help...
Thanx in advance, debmalya_92

---

### Post by vandamme on 2011-01-26
The program you need is GParted. Look under System-> Administration ->Gparted partition editor. If it's not there use the Ubuntu Software Center to install it. 
It has a pretty good help file, so have fun with it.

---

### Post by Rubi1200 on 2011-01-26
Hi and welcome to the forums debmalya_92 :-)

It would be helpful if you told us how big the drive is and what exactly you want to do.

You can install GParted as vandamme, but I recommend you take a screenshot first of the setup once you install and open GParted and then post it here so we can offer you advice on the best partitioning scheme for your needs.

---

### Post by debmalya_92 on 2011-01-26
Thanx for the replies guys
I have a dual boot of ubuntu 10.10 and windows xp sp2
Forget the xp part, I have a 40 gb partition for ubuntu. But I want to divide it further into 2 partitions of 20 gb each without reinstalling so that i can keep my files into 1 and it doesn't get mixed with the bootable parts...

I am installing Gparted as u suggested, will post a screenshot soon asking for further help

---

### Post by Mark Phelps on 2011-01-26
If you're talking about resizing the partition you're using while running Ubuntu -- you can't do that.  That partition must be mounted to be used, and mounted partitions can't be modified.

You can either boot from an Ubuntu LiveCD and use Partition Editor on that to do the resizing (just make sure NONE of the partitions are mounted, including the Swap partition), or you can download and burn a GParted LiveCD (which you can get from distrowatch.com) and use that.

Personally, I prefer the latter because it prevents problems with partitions being mounted and it is always the latest version.

---

### Post by debmalya_92 on 2011-01-26
Do i have to use the Gparted live CD?? I am installing it from the software centre...
I mean to resize it, yes

---

### Post by Zanderist on 2011-01-26
You can use the gparted in the live CD.

Just don't change the flags.

---

### Post by debmalya_92 on 2011-01-26
Do i have to use the live cd??? I mean is it compulsory, or will it work from the sysem itself??

---

### Post by Quackers on 2011-01-26
As Mark Phelps said earlier, if you try to use gparted for this purpose from the installed system, it will not allow it, as the file system is already mounted. In fact, if it did allow it, you may be in for trouble!
Gparted from the Ubuntu live cd is better, and , possibly, gparted from its own live cd is best.
Before making changes you should right-click the swap partition and select "swapoff".

---

### Post by debmalya_92 on 2011-01-26
Thanx u all...
Just one last question to be sure - Using the gparted live cd to resize my partition won't affect my installation, will it???

---

### Post by Rubi1200 on 2011-01-26
First, make backups of all important data before you start anything.

Second, post a screenshot se we can see what you have and can offer better advice.

There is always a certain amount of risk involved with partitioning, but if you are careful then it should all be good.

---

### Post by ajgreeny on 2011-01-26
It certainly shouldn't, but make sure you back up first.  You should always back up when carrying out any partition changes, no matter what tool you use to do it.

Things seldom do go wrong in my experience, but you can bet your boots, if you have no back ups, that's when it will all go pear-shaped.

---

### Post by debmalya_92 on 2011-01-26
thanx 2 all of u who replied me...
I will try it out, and let u people know what happens :D

---

