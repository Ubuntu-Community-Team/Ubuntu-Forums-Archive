---
title: "Boot partiton too small"
date: 2009-10-06
forum: General Help
---

### Post by thebrandon on 2009-10-06
I foolishly only allocated 5 gigs for my ubuntu boot partiton and I am now having some trouble with running out of space I assume because some of my apps need temp space on that partition.  As far as I know I cant resize the partition without the risk of data loss and I dont really want to do a reinstall and all of that.  Is there a way I can redirect my applications to use temp space on one of my larger partitons.  The applications in question, I belive anyway, are Deluge, Miro, Firefox, and Thunderbird.  I have deleted some of the stuff that comes installed that I dont use so that helped but I currently only have about 600 mb left.  Any suggestions as to how to improve my situation would be greatly appreciated!  Thanks!

---

### Post by Giblet5 on 2009-10-06
First, make /home a separate partition (if you haven't already).

Then, make /tmp a separate filesystem.

The best fix is to reinstall on a larger partition. Heck, 5GB will make a nice second swap partition!

Note: If you run less than 10% free, you'll notice a dramatic performance drop on writes.

---

### Post by drs305 on 2009-10-06
I've written a couple of things that may help.

First, although there is always a risk, many of us have resized system partitions without any problems. Just backup important data first in case something does go wrong. Here is a post for expanding the / partition. I wrote it to help with a bug that created a 2.5GB system partition, but everything applies to larger partitions as well.
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

This second post deals with finding lost disk space. Although you know why your partition is filling up, you may find some of the sections useful in trimming down what's already located on your partition:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

You also have the option of moving your /home partition. There are plenty of links for that.

Best of luck whatever path you take.

---

### Post by thebrandon on 2009-10-08
Well I ended up resizing that 5 gig partition to about 20 gigs.  Thanks for your help!

---

