---
title: "Advise on Ubuntu 10.10 Reinstall"
date: 2011-06-16
forum: General Help
---

### Post by tej1984 on 2011-06-16
There comes a time when some users like myself will end up destorying there wonderfull workspace by editing files and not knowing what they are doing. 
 
I ask all you users what would you do different when installing Ubuntu again from fresh? 
 
I.e Partitioning the hard drive - which I didnt do? 
 
How do you partition as I have looked at many forums and not been able to do it? 
 
Which version of ubuntu would you install if you had the chance 10.4/10.10/11.04 
 
or Can a version of ubuntu be repaired by doing a system restore at the installation point?

---

### Post by nothingspecial on 2011-06-16
I would have a 10-12 gig / partition

I would then have a /home partition that allowed 2-3 gigs per user.

I would have a 4 gigabyte swap partition

The rest of the space would then be a data partition.

I would use symbolic links to access the data (media, docs, photos etc) on the data partition from each users home.

I would back up the home partition weekly (not following the links to the data partition).

Then, if I completely stuff up my system, I can simply copy a back up of home if I have changed some personal setting and don't know how to fix it and/or reinstall the operating system to the / partition.

---

### Post by tej1984 on 2011-06-16
> **nothingspecial said:**
> I would have a 10-12 gig / partition

I would then have a /home partition that allowed 2-3 gigs per user.

I would have a 4 gigabyte swap partition

The rest of the space would then be a data partition.

I would use symbolic links to access the data (media, docs, photos etc) on the data partition from each users home.

I would back up the home partition weekly (not following the links to the data partition).

Then, if I completely stuff up my system, I can simply copy a back up of home if I have changed some personal setting and don't know how to fix it and/or reinstall the operating system to the / partition.
Great advice nothingspecial how do I partition? when I try and install ubuntu i try to partition the drive but it does not let me? any ideas?

---

### Post by nothingspecial on 2011-06-16
I sometimes think it's easier to partition from the live cd using the partition editor before you install rather than trying to do it during the installation process itself.

---

### Post by tej1984 on 2011-06-16
> **nothingspecial said:**
> I sometimes think it's easier to partition from the live cd using the partition editor before you install rather than trying to do it during the installation process itself.
the thing is I have an Acer Revo which does not come with a CD drive so what i have done is install a live CD Usb version and then tryied to configure it at the installation menu using the partition editor but it just doesn't let me. I can just set everything as my home dir but not partition. AHHRRR!!!

---

### Post by coldraven on 2011-06-16
You could download Parted Magic (170MB) from here [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)
Follow the instructions to make a bootable USB disc or use the System>Admin>"Startup Disc Creator" from Ubuntu.
It's basically using the same Gparted that is on the Ubuntu Live CD but with some extra tools.
It will boot up quicker than an Ubuntu CD and is a handy thing to have in your toolbox for fixing PCs.
Gparted is easy to use, no matter what partitions you experiment with making, nothing actually happens until you click "Apply" at the top of the screen. So you can Undo any changes before you commit yourself.
So if you are planning to erase everything you can't go wrong, just start by right clicking and select "Delete partition". Have fun, read the manual! :)

---

