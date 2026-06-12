---
title: "using gparted"
date: 2010-02-04
forum: General Help
---

### Post by wcutrombonekid on 2010-02-04
so i downloaded gparted.  i would really like to make my ubuntu partition bigger, i've got over 200 gigs of free space on my windows partition.  i've played with it some and cannot seem to figure out what to do.

anyone know of a tutorial?

thanks
chris

---

### Post by cenzorrll on 2010-02-05
you'll need to use the livecd if you want to change the size of your ubuntu partition.  this is because you need to unmount the filesystems before you can change them, and you can't unmount the filesystem you're using.

you can download the gparted livecd from their website, or you can use the ubuntu installer cd (so long as you have the desktop version, not alternate or server, if you don't know then you probably have the desktop version)

then you can use gparted to change the size of your partitions. BE VERY CAREFUL. gparted is very powerful and it is easy to destroy all your data and wipe your hard drive. i would suggest backing up all important files from ALL of your partitions to a separate disk.

do not interrupt any processes until they are finished, otherwise say goodbye to your data.

besides that, have fun.

---

### Post by tom.swartz07 on 2010-02-05
> **cenzorrll said:**
> you'll need to use the livecd if you want to change the size of your ubuntu partition.  this is because you need to unmount the filesystems before you can change them, and you can't unmount the filesystem you're using.

you can download the gparted livecd from their website, or you can use the ubuntu installer cd (so long as you have the desktop version, not alternate or server, if you don't know then you probably have the desktop version)

then you can use gparted to change the size of your partitions. BE VERY CAREFUL. gparted is very powerful and it is easy to destroy all your data and wipe your hard drive. i would suggest backing up all important files from ALL of your partitions to a separate disk.

do not interrupt any processes until they are finished, otherwise say goodbye to your data.

besides that, have fun.

I concur. Just to reiterate; You could run gParted from a LiveCD or even from an Ubuntu LiveCD; you just cannot have an installed OS running at the time that you edit the partitions.



Make absolutely sure that you know what changes you are doing, and only apply them one at a time. (for example, shrink Windows-apply, move Windows- apply, expand ubuntu- apply, rather than all at once.)

ADDITIONALLY- before you begin, make sure that you run a system cleanup on Windows. Defrag the drive, use system janitor, etc. Sometimes files may be fragmented towards the end of the partition and will be lost when the filesystem shrinks.


Its not a difficult task to change the size of your partitions, its just a very tedious and concentration demanding process. Give yourself a good hour to sit down with no distractions and work on it, and youll be fine.

---

### Post by wcutrombonekid on 2010-02-05
i did not know that, but it makes sense.  i appreciate it, thanks guys

---

### Post by audiomick on 2010-02-05
Another alternative that you should be able to do from a running system is to simply create a new partition in the empty space, and then make that available to your Ubuntu install.
I think you need to change fstab to make the mount permanent.

---

### Post by drs305 on 2010-02-05
> **wcutrombonekid said:**
> 
anyone know of a tutorial?

thanks
chris

[Expanding /]("http://ubuntuforums.org/showthread.php?t=1219270")

Written for a Jaunty bug but the procedure still applies. See the second half of the first post.

---

