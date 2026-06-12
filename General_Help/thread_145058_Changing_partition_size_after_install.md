---
title: "Changing partition size after install?"
date: 2006-03-15
forum: General Help
---

### Post by tgoose on 2006-03-15
Well it seems that, like a fool, I didn't leave enough space for my / mount. Now there's plenty of unused space in the partition that mounts to /home, but it's obviously not very useful when I can't put anything on /. Now, I'd quite like to repartition so that some of that free space can be put on the / partition. I've tried gparted in Ubuntu but with no luck, presumably because the drive has to be mounted to load Ubuntu. I've heard people talk of a live CD with something to partition with on it? If that can do some nondestructive repartitioning without Ubuntu being loaded could some kindly soul please point me in the right direction?

---

### Post by Xian on 2006-03-15
They are referring to the [Gparted LiveCD](http://gparted.sourceforge.net/livecd.php).
Be sure to make backups and read the documentation.

---

### Post by OBnascar on 2006-03-15
[QUOTE=Xian]They are referring to the [Gparted LiveCD](http://gparted.sourceforge.net/livecd.php)[/QUOTE]

I have never seen this Gparted LiveCD mentioned before, thanks Xian.

I also have been looking for a partimage live CD, for that I use the SystemRescue CD, which is ok but for some reason I would like to have it on a CD by itself. Have you ever heard of such a thing ?

---

### Post by tgoose on 2006-03-16
Ok, I've booted from gparted and it loads up fine. The problem now is that the empty space is before the partition I want to increase. I've been thinking of ways to deal with these and have thought of two alternative routes:

1) back up all data to an external drive, in their actual partitions, then resizing them and moving them back (possibly all within gparted)

2) create yet another mount point on something like /usr, then shift stuff back around afterwards.

Thanks for letting me know about the live CD; I'll be back again if I have any problems ;)

---

