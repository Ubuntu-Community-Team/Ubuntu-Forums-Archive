---
title: "Need Help , about raw partitioning"
date: 2010-06-30
forum: General Help
---

### Post by hengchuen on 2010-06-30
Hi everyone. There is 1 question over here. Currently my Window XP has all the hard disk space. How can I create back a raw partition so I can dual boot uBuntu??

I heard there is a tool called magic xxxxxxx.. forget the name >.< or any better way?

Thanks...

Regards,
hengchuen

---

### Post by justleen on 2010-06-30
Partition magic.

Normally I would boot from a live-cd, install gparted, and resize it through there.

---

### Post by Rubi1200 on 2010-06-30
GParted is installed by default on the LiveCD. It is a great tool for working with partitions.

Make sure you backup any important data BEFORE resizing partitions; there is always the risk of data loss.

---

### Post by Seth-666 on 2010-06-30
I want to install ubuntu on my PC, but at this time a have Windows 7 and  the partitions are for wn 7, if i install Ubuntu do i have to do the  partitions from 0?

---

### Post by Rubi1200 on 2010-06-30
See this:

[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

and this:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

This should answer most questions. If not, feel free to ask on the forum. 
But I suggest you start your own thread.

---

### Post by ramnarayan on 2010-06-30
> **hengchuen said:**
>  How can I create back a raw partition so I can dual boot uBuntu??


what do you mean by Raw partition

**
If you want to do any partition boot up using a live cd  (Ubuntu) and use gparted

is most cases this should do the job.

Before installing Ubuntu just read up on partitioning

ram

---

### Post by Seth-666 on 2010-06-30
a want ubuntu to be the only OS on my pc and i want to know if i really need to do the partitions again?

---

### Post by Rubi1200 on 2010-06-30
> **Seth-666 said:**
> a want ubuntu to be the only OS on my pc and i want to know if i really need to do the partitions again?

If that is the case, though I suggest you seriously consider whether you **really** want to do that, when you choose to install Ubuntu from the CD pick the option to Erase and use entire disk for Ubuntu. That will delete Windows permanently!

Unless you have the installation CD for Windows, I suggest you try dual-booting first to see if you really want Ubuntu as your primary, and only, OS.

---

### Post by justleen on 2010-06-30
Windows 7 can resize the partition too, on the fly, via the disk manager  (even the system partition! they do have come a long way...)
In older versions of the live cd gparted wasn't installed, did'nt know it was nowa days.

I think he means an empty partition (at least, all my posts assume he does :)

---

### Post by Seth-666 on 2010-06-30
> **Rubi1200 said:**
> If that is the case, though I suggest you seriously consider whether you **really** want to do that, when you choose to install Ubuntu from the CD pick the option to Erase and use entire disk for Ubuntu. That will delete Windows permanently!

Unless you have the installation CD for Windows, I suggest you try dual-booting first to see if you really want Ubuntu as your primary, and only, OS.

i did that, i have used the Wmware for adding linux just for testing, and i really want to learn linux, what can i do on it and what Not... everything

---

### Post by ramnarayan on 2010-06-30
> **Seth-666 said:**
> a want ubuntu to be the only OS on my pc and i want to know if i really need to do the partitions again?

Seems like quite a few people have the same question

see [http://ubuntuforums.org/showthread.php?p=9529664#post9529664](http://ubuntuforums.org/showthread.php?p=9529664#post9529664)

and see below
ust pop ubuntu live cd in boot up

then go to system - administration - gparted

once this opens up -just select each partition and delete them one by one.

80 gig is a lot

MAKE SURE YOU BACK UP ANY DATA YOU HAVE

**
After that you can
either close gparted and begin the instal from the desktop icon

or continue in gparted and set you partitions up before hand (i do this)

**
Partitioning
So if you use gparted (or if using the install partitioner - select manual mode)

This will be my partition scheme (assuming that no other OS is being left)

1. 100 MB for /boot use ext4 file system
2. 1024 MB (for Swap)
3. 12 Gig for / (called your root - where you OS is)
4. the remaining can be /home (where your data is)

If you like playing around and experimenting with the latest you could choose to be another partition of 12 GB available for a second OS (linux ) to be dual booted.

I prefer Using gparted to do all this first because it allows you to structure your partitions. You are allowed only 3 primary. Which means if you use the above you actually have 4 or 5

So your 3rd partition has to be extended and under this you can have as many as you want.

If you want to be flexible keep your /home in a separate primary and arrange the rest as you wish

After this partitioning is done (preferably using gparted) then get on with your install

and then enjoy

ram

---

### Post by Rubi1200 on 2010-06-30
> **Seth-666 said:**
> i did that, i have used the Wmware for adding linux just for testing, and i really want to learn linux, what can i do on it and what Not... everything

In other words, Windows is gone?

If you want to learn Linux, and Ubuntu specifically, then start with some of these links:

[http://sites.google.com/site/easylinuxtipsproject/Home](http://sites.google.com/site/easylinuxtipsproject/Home)

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

[http://ohioloco.ubuntuforums.org/showthread.php?t=801404](http://ohioloco.ubuntuforums.org/showthread.php?t=801404)

Good luck!

:-)

---

### Post by Rubi1200 on 2010-06-30
> **ramnarayan said:**
> Seems like quite a few people have the same question

see [http://ubuntuforums.org/showthread.php?p=9529664#post9529664](http://ubuntuforums.org/showthread.php?p=9529664#post9529664)

and see below
ust pop ubuntu live cd in boot up

then go to system - administration - gparted

once this opens up -just select each partition and delete them one by one.

80 gig is a lot

MAKE SURE YOU BACK UP ANY DATA YOU HAVE

**
After that you can
either close gparted and begin the instal from the desktop icon

or continue in gparted and set you partitions up before hand (i do this)

**
Partitioning
So if you use gparted (or if using the install partitioner - select manual mode)

This will be my partition scheme (assuming that no other OS is being left)

1. 100 MB for /boot use ext4 file system
2. 1024 MB (for Swap)
3. 12 Gig for / (called your root - where you OS is)
4. the remaining can be /home (where your data is)

If you like playing around and experimenting with the latest you could choose to be another partition of 12 GB available for a second OS (linux ) to be dual booted.

I prefer Using gparted to do all this first because it allows you to structure your partitions. You are allowed only 3 primary. Which means if you use the above you actually have 4 or 5

So your 3rd partition has to be extended and under this you can have as many as you want.

If you want to be flexible keep your /home in a separate primary and arrange the rest as you wish

After this partitioning is done (preferably using gparted) then get on with your install

and then enjoy

ram

To be honest, I don't think suggesting partitioning schemes like this is helpful for beginners; there is too much that could *potentially* go wrong. The default installation as set up by Ubuntu should satisfy *most* people's needs.

---

### Post by Seth-666 on 2010-06-30
I want to make the C: partition for linux and the second D: i want to leave it exactly is it now with music, documents, programs, is there going to be a problem?

---

### Post by Rubi1200 on 2010-06-30
Take a look here:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Abu Azzubair on 2010-06-30
I learned from this Link:

[http://www.youtube.com/watch?v=PUZqF5fyrJo](http://www.youtube.com/watch?v=PUZqF5fyrJo)

I found it easy and strait forward

I hope it's in the subject :-/

---

