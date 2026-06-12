---
title: "Expanding partition and restoring image"
date: 2011-03-10
forum: General Help
---

### Post by Hero1969 on 2011-03-10
Here is the scenario:

I have triple boot
Win 7 32 bit on hard drive 1
Win 7 64 bit on hard drive 2
Data partition accessible by 3 OSs
Ubuntu 10.10 on hard drive 2


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60801   488280064    7  HPFS/NTFS



   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14663   117779456    7  HPFS/NTFS
/dev/sdb2           14664       79973   524595132+   7  HPFS/NTFS
/dev/sdb3           79973       91202    90195969    f  W95 Ext'd (LBA)
/dev/sdb5           79973       90671    85936128   83  Linux
/dev/sdb6           90672       91202     4258816   82  Linux swap / Solaris


Everything is working great.  I'm using Windows Boot Loader (used easybcd to attach Ubuntu).

I want to expand /dev/sdb3 to have more space for Ubuntu.  I am able to shrink the data partition /dev/sdb2, which leaves an unallocated space.  I have backed up /dev/sdb3 using Paragon software.  

My question is, what is the best way to expand the /sdb3 partition into the unallocated space and restore the ubuntu image backup so that it will use up all the space (unallocated and current /sdb3)?  I don't want to screw up since everything is working properly, I just want some more space.

---

### Post by lithopsian on 2011-03-10
Ideally back up both sdb2 and sdb3.  You can probably shrink one and grow the other and keep your data intact, but after they are trashed is too late to change your mind.

I would use gparted from a Live CD, then you will be able to change anything you like.  In your case, can sdb2 and sdb3 be unmounted while Ubuntu is running?  Looks like they are just data mounts?  Then you could run gparted from your normal Ubuntu session.

Afterwards, everything should still be in place.  If not then you'll have to restore from your backup.

---

### Post by Hero1969 on 2011-03-10
Picture gparted graphically.  I can move the right edge of sdb3 to the left (about 50gb).  Which leaves 50gb unallocated space.  So then I try to move the left edge of sdb3 (currently about 100gb) to the left to fill up the unallocated space but it doesn't work.  I've tried gparted live cd, easus and even windows disk manager.

What I'm thinking of doing is deleting sdb3 (which includes the sdb5 and sdb6/swap).  But here is where I'm stuck.  Now I will have 150gb unallocated space.  When I restore the back up will it automatically fill in this space and create correct partitions or should I create the partitions first and then restore.

---

### Post by lithopsian on 2011-03-10
I see.  Older versions used to do this, but you have Maverick.  Which version of gparted are you running?

Another possibility is that you are trying to expand one extended partition to include space from a different extended partition.  I can't tell from your partition listing if this is the case.

The latest releases of gparted can certainly expand (and shrink) in any direction.  You can download a LIVE CD version of gparted direct from their web page if you think you have an old version and can't get a new one.

---

### Post by Hedgehog1 on 2011-03-10
```

Device Boot Start End Blocks Id System
/dev/sdb1 1 14663 117779456 7 HPFS/NTFS
/dev/sdb2 14664 79973 524595132+ 7 HPFS/NTFS
[COLOR="Red"]/dev/sdb3 79973 91202 90195969 f W95 Ext'd (LBA)[/COLOR]
[COLOR="YellowGreen"]   /dev/sdb5 79973 90671 85936128 83 Linux
   /dev/sdb6 90672 91202 4258816 82 Linux swap / Solaris[/COLOR]

```

**lithopsian** is correct, you need to move/expand the [COLOR="red"]/dev/sdb3 extended parition first[/COLOR], then you cam move/extend your [COLOR="YellowGreen"]/dev/sdb5[/COLOR] parititon.

To do this you must boot from a LiveCD or LiveUSB.  Select 'try' and fire up gparted.

You may have to right click on the [COLOR="YellowGreen"]/dev/sdb6[/COLOR] and select 'swapoff' to get the [COLOR="red"]/dev/sdb3[/COLOR] unmounted if it is still mounted even after booting from the LiveCD/LiveUSB.

[SIZE="3"]Visual Aid:[/SIZE]
[IMG]http://img88.imageshack.us/img88/8340/dualbootdmview.png[/IMG]

***The Hedge***

:KS

---

### Post by Hero1969 on 2011-03-10
Thanks, 

One of those duh moments.

---

