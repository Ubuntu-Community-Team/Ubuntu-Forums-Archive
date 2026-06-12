---
title: "How do I remove unused space from Ubuntu partition?"
date: 2011-06-14
forum: General Help
---

### Post by DrKnobblez on 2011-06-14
Here's my dilemma. I'm trying to Dual-boot Windows and Ubuntu. I have Ubuntu now.** I'm trying to remove space from the Ubuntu partition(Active) but, it won't allow me to remove space from active partitions.** I have 11GB Free according to GParted, yet during the installation it displays only 8MB Free. Oh, and I'm trying to install Windows XP through VirtualBox. Is that possible through the install CD? I've been searching and haven't seen anything about it.  O.o

---

### Post by pqwoerituytrueiwoq on 2011-06-14
if it on on the far left on the drive to not bother with it (by unused i assume you mean unallocated)
if it is on the right side you can try to grow the partition 
live cd open gparted system->administration->gparted

---

### Post by DrKnobblez on 2011-06-14
I meant I have 11GB of unallocated. The rest is allocated to the Ubuntu partition. I need to take some of the unused data in the Ubuntu partition and un-allocate it.

---

### Post by wildmanne39 on 2011-06-14
> **DrKnobblez said:**
> I meant I have 11GB of unallocated. The rest is allocated to the Ubuntu partition. I need to take some of the unused data in the Ubuntu partition and un-allocate it.Hi, I am going to give you a link for partitions, and about virtualbox your question is a little unclear but I am going to give you a link that will answer all your questions, I personally use virtualbox and a like it a lot. You can install xp if you have a xp disk and virtual box is installed, but you made it sound like you were running ubuntu with an install cd. Please read all about virtualbox before you start the install it will save you a lot of trouble.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by DrKnobblez on 2011-06-14
Thank you for your help but, the problem is that the partition I want to resize is currently mounted. I have Ubuntu installed on this partition. I'm not using an Ubuntu install CD to run Ubuntu. I do not have enough unallocated space(11GB) to install Windows. When I use GParted, I right-click on the Ubuntu partition and all options are unavailable(gray) except Unmount, Manage Flags, and Information.

---

### Post by pqwoerituytrueiwoq on 2011-06-14
you can resize from a live cd/usb
there is a chance something could backfire so back anything important up

---

