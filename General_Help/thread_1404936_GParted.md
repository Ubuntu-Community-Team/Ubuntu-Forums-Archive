---
title: "GParted"
date: 2010-02-12
forum: General Help
---

### Post by Captjac91 on 2010-02-12
Hey guys quick question for you all, I'm Dual Booting Ubuntu and Vista and i downloaded gparted today because i wanted to resize my operating systems so that Ubuntu had the majority of the hard drive. I was able to resize the vista part so that it was smaller, however i can't figure out how to resize the ubuntu half so that it takes up the unallocated part. if someone could help me to figure this out it would be very appreciated :D. I am currently in the process of changing over completely to ubuntu but i dont want to get rid of vista completely just yet.

---

### Post by Satoru-san on 2010-02-12
[s]What filesystem are you using on ubuntu?[/s]
I missunderstood, you haven't installed ubuntu yet.

When you install it, you can choose to install it in the free space that you made

---

### Post by bobpress on 2010-02-12
By downloading do you mean added to your Ubuntu or as a .iso image you burned to a CD and booted from?  You cannot change the partitions that are in use.  You were able to change Vista since it was not mounted and was not in use.  GParted on a Live Ubuntu CD can be used to change the partitions on your Hard Drive.

---

### Post by Mark Phelps on 2010-02-12
> **Captjac91 said:**
> ...I am currently in the process of changing over completely to ubuntu but i dont want to get rid of vista completely just yet.

Well, for your sake, I hope you're one of the lucky few that did NOT corrupt your Vista OS when you used GParted to shrink the partition.

Before you do anything else, you should boot back into Vista and confirm that it still boots and runs OK.

---

### Post by OrangeCrate on 2010-02-12
> **Mark Phelps said:**
> **Well, for your sake, I hope you're one of the lucky few that did NOT corrupt your Vista OS when you used GParted to shrink the partition.**

Before you do anything else, you should boot back into Vista and confirm that it still boots and runs OK.

Adding to Mark's post...

You should review these instructions on dual booting before you go much further:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

Particularly here:

[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

---

### Post by Captjac91 on 2010-02-12
At this point i kinda don't care if vista gets corrupted i have it all backed up and my laptop isn't my main machine so it doesn't make much of a difference it something goes wrong anyway but what i'm asking is, is there any way to make ubuntu take up the rest of the space on my hard drive? because right now i have a  unallocated section on my hard drive that doesn't have anything on it and i want ubuntu to take that empty space up. is that possible?

---

### Post by oldfred on 2010-02-12
You need to use a liveCD and even then the liveCD's mount the swap partition to speed up the cD. Click on the swap partition in gparted and rightclick, swapoff. That should remove the key symbols that show the partitions are locked.

---

### Post by mkvnmtr on 2010-02-12
Gparted can not be used on a partition that is mounted. That means you have to use it on a live disk to work on your partitions. If you are using it from a distro on your machine you can work on other partitions but it will be a bit slower than from a live disk. I always install it but for use on external hard disks.

---

