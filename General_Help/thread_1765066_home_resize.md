---
title: "/home resize"
date: 2011-05-22
forum: General Help
---

### Post by maki5 on 2011-05-22
Hi! 
I just moved on ubuntu from windows, in windows I had 3 partitions, when I install ubuntu I mounted first in / the second in /home, after install it I move my data from third partition and format it to ext4, now I want to delete it and resize /home partition, I try gparted but first I need to unmount my /home and can't do it, anybody knows how to do this resize?

---

### Post by Hedgehog1 on 2011-05-22
Whenever you need to make changes to partitions, you need to not be mounted to them.

We normally boot from the LiveCD/LiveUSB, select 'TRY' and use gparted from the LiveCD/LiveUSB to make changes to the disk drive's partitions.


***The Hedge***

:KS

---

### Post by lithopsian on 2011-05-22
You can do it from the console (text or recovery boot), but the Live CD is much easier (but a little slower).

---

### Post by keikoh on 2011-05-25
> **maki5 said:**
> Hi! 
I just moved on ubuntu from windows, in windows I had 3 partitions, when I install ubuntu I mounted first in / the second in /home, after install it I move my data from third partition and format it to ext4, now I want to delete it and resize /home partition, I try gparted but first I need to unmount my /home and can't do it, anybody knows how to do this resize?

You need to boot from GParted. Try this [link.]("http://taidanielpc.blogspot.com/2011/05/how-to-organize-and-partition-your-hard_23.html") It boots GParted from USB.

---

### Post by aeiah on 2011-05-25
you seem like the type that'd know this already, but make sure everything is backed up. ive had partition resizes go wrong in the past.

the gparted livecd/usb is probably your best course of action. smaller and quicker than a full blown ubuntu livecd, and just contains gparted and a few other tools.

---

