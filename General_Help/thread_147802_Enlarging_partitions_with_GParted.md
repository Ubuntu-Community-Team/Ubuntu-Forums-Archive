---
title: "Enlarging partitions with GParted?"
date: 2006-03-20
forum: General Help
---

### Post by Leiki on 2006-03-20
I'd like to make my Windows partition smaller and enlarge my Ubuntu partition. I downloaded the GParted live cd and ran it. I was able to successfully shrink my Windows partition, however it won't let me enlarge my Ubuntu partiton. I now have around 30 GB of unallocated space! So...any one know a way to resize it bigger? Thanks for your help.

---

### Post by cilynx on 2006-03-20
I'm assuming that your Ubuntu partition is at the end of the drive, right?

You need to move it first such that it butts up against your Windows partition, then you can resize it larger.  You can only add size to a partition on the end as opposed to the beginning.

This can all be done pretty easily with gParted

---

### Post by Leiki on 2006-03-20
Yes, my Ubuntu partition is at the end. This might be a dumb question, but how do I "switch" my partitions?

---

### Post by cilynx on 2006-03-21
I'm pretty sure gParted has a "move partition" feature.  You don't need to switch them, you just need to push the Linux partition to the left a bit.

I'm guessing your gParted looks like this:

[----------Windows----------][---empty---][-----Linux-----]

You need to move the partitions like so:

[----------Windows----------][-----Linux-----][---empty---]

You can then resize to:

[----------Windows----------][-------------Linux-------------]

Make sense?

---

### Post by akiro.yamamoto on 2006-03-21
You may have to use a live cd.
In order to resize a partition you will have to unmount it before you can work on it.
See the attached pics ;)

---

### Post by terranz on 2006-03-22
Am I to understand from this thread that linux will not die and kernel panic on me anymore if I change a partition size?

---

### Post by sands on 2006-03-22
Hey I'm havin a single ubuntu partition..
Is it possible to make a split...

Not to install the Microsoft thing..Just 4 my curiosity..

---

### Post by plors on 2006-03-23
[QUOTE=terranz]Am I to understand from this thread that linux will not die and kernel panic on me anymore if I change a partition size?[/QUOTE]

it would certainly help if you would use the latest [gparted livecd]("http://gparted.sourceforge.net/livecd.php") instead of the (very old) version on the ubuntu livecd :D 

have fun.

---

### Post by justleen on 2006-03-23
[QUOTE=sands]Hey I'm havin a single ubuntu partition..
Is it possible to make a split...

Not to install the Microsoft thing..Just 4 my curiosity..[/QUOTE]

Yes.. as long as you have enough freespace that is.
you could shrink a partition, create a new partition on the free space and  mount it to /home, for example

---

### Post by groggyboy on 2006-03-23
i checked out the gparted website.  according to the nifty little table, gparted can't move ext3 or ntfs partitions!  only copy.  doesn't this kinda complicate things?  just asking, cuz i have plans to rearrange the partitions on my hd, and wanna do it with a minimum of hassle.

cheers!

---

### Post by Barrakketh on 2006-03-23
There is a bug with the version of parted and libparted that is used in Breezy and Dapper (I don't think it was ever patched in Dapper, and it wasn't upgraded).  Attempting to resize either an ext2 or ext3 filesystem will give you this error:
> No Implementation: This ext2 file system has a rather strange layout!  Parted can't resize this (yet).
It's fixed in a CVS build.

FYI, it's possible to remove the journal from an ext3 filesystem (thus making it ext2) and later recreate it.

---

### Post by terranz on 2006-03-23
[QUOTE=plors]it would certainly help if you would use the latest [gparted livecd]("http://gparted.sourceforge.net/livecd.php") instead of the (very old) version on the ubuntu livecd :D 

have fun.[/QUOTE]

8) I downloaded it yesterday after learning of it.  Now I have an answer I'll do some resizing.

---

