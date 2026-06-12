---
title: "Allocate free space to Windows partition without moving Linux partition?"
date: 2012-05-20
forum: General Help
---

### Post by pepperjinks on 2012-05-20
I'm trying to allocate more free space to my Windows partition. Here's what my setup looks like in GParted:

[IMG]http://i.imgur.com/vpEi6.png[/IMG]

Is it possible for me to allocate free space to my Windows partition without having to move the entire Ubuntu partition to the right?

Thanks in advance.

---

### Post by agillator on 2012-05-20
Short answer: no.

In order to enlarge the windows partition there must be space next to it available. So, you will have to move the linux partition or resize it leaving the unused space at the beginning of the current partition or something to create room to expand the windows partition.

---

### Post by Mark Phelps on 2012-05-21
If you still want to expand the size of the Windows partition, you should do it as follows:
1) Boot from an Ubuntu LiveCD or GParted LiveCD.  You need to do this because you can't alter partitions that are in use -- which is the case if you boot into Ubuntu on your hard drive.
2) Use GParted to move the Ext4 partition to the right.
3) Use GParted to shrink the Extended partition to the right
4) THIS IS IMPORTANT -- boot into Win7 and use the Disk Management utility to expand the Win7 partition to take up the free space.  Do NOT use GParted to do this -- using GParted will risk corrupting the Win7 OS filesystem.

---

