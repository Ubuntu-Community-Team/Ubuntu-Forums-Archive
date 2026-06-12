---
title: "Really need more space. Help resizing?"
date: 2012-09-26
forum: General Help
---

### Post by lemonoid on 2012-09-26
So my Ubuntu is out of disk space. I started taking care of this problem a few weeks ago when I got my desktop back up and running and pretty sure I know what I need to do, but I have a couple of questions. I have always just booted into live Ubuntu to resize partitions, but if I have a live GParted to boot, I can just boot straight to that, correct? Also, do I need to put in Boot Repair and fix boot problems every time I resize my partitions? Previously I was trying to delete other partitions not currently in use, and then stretch the one in use, so the first time I just deleted a partition (old version of Linux Mint), and when I booted my computer up, my boot was broken so I made a boot repair disk. The second time I booted into Live Ubuntu, deleted a partition, and I believe I stretched the one I'm currently on, and when I tried to boot up, once again, my bootloader was broken and I had to use Boot Repair to fix it. Currently I have Windows 7 installed beside Ubuntu 12.04, with about 8GB of unused space at the end of this partition. I would like to shrink my Windows down probably ten or 15 GB, so that I have around 20 or  25 GB of space that I can use for my Ubuntu. Is there anything I can do to keep from having to use Boot Repair when I resize my partitions? Do I need to boot into Windows to shrink that volume? Thank you in advance for your assistance.

[ATTACH]224681[/ATTACH]

---

### Post by zvacet on 2012-09-27
I think Windows 7 have tool for partition resizing.Use it.After that you can expand your extended partition on that unallocated space using Gparted.i don´t think you will have to use boot repair,because you are just shrinking partitions,not deleting them.

---

