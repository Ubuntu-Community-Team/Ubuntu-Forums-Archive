---
title: "Ubuntu Disks Space Confusion"
date: 2011-06-22
forum: General Help
---

### Post by GodveX on 2011-06-22
I recently decided to wanted to switch from windows to ubuntu 11.04 since linux can do the same work as windows for me

While going with a fresh installation of linux by itself i noticed that instead of my original laptop hdd space of 350gb it said allocated 320gb i went with the install and now that it is ready the disk manager says i have 280gb space what is this please ?

Should i re install ubuntu to get the missing hd space ?

---

### Post by FormatSeize on 2011-06-22
> **GodveX said:**
> Should i re install ubuntu to get the missing hd space ?
 
Before you do that, have a look at your partition table and see where the space is allocated. Go to a terminal and use the following command (while ***not*** logged in as root):
```
cfdisk
```
This will bring up your partition table and show you where your disk space is allocated. What I am suspecting is that it is showing you 280GB because the system is set up to show you only space that is directly available to the user, and is not showing things like a boot partition, swap partition(s), and extended partition(s). 
 
I came across something similar to this over the weekend. I bought a brand new machine which on the box said that it had 500 GB of space on the hard drive. When I got home, it said that it only had 325 GB. Now being used to only 40GB hard disk space, this would be tons of space, but having spent the money for 500, I wondered about it. When I took a look at the partition table, it was only showing the 325 that was allocated for the "C" drive, while the rest was in a boot partition, a swap partition (I'm assuming that's what it was), and the rest was just free space.
 
All in all, I don't think that Ubuntu shrank your hard disk, but rather it's not showing you things that a normal user would never have to access.

---

### Post by oldfred on 2011-06-22
Your hard drive is not 350GiB but only 350GB.

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by GodveX on 2011-06-22
thanks for your great replies guys i can understand now why the disk space only shows 289GB now :P 

so theres no need to re install this wonderful OS

---

