---
title: "dd cloning"
date: 2009-09-18
forum: General Help
---

### Post by ub007 on 2009-09-18
Hi All,

I'm trying to clone 2 raid sets using dd

as an example
> dd if=/dev/sda of=/dev/sdb

the default block size is 512bytes. I increased it to 256K and still takes 9 minutes to image 1GB. I need to clone 7T and this would take weeks.

How much can I increase the ' bs ' without affecting the layour of the disks???
I realize that the maximum size of a physical write call in unix is 256k. Any ideas folks??

---

### Post by StuartN on 2009-09-18
> **ub007 said:**
> the default block size is 512bytes. I increased it to 256K and still takes 9 minutes to image 1GB.

The bottle-neck is not your block size. This is a little slow - 1 GB in 9 minutes is 1.85 MB per second. Something in your path is capping this, and will not change with block size. Uncontested (100 Mbit/s) ethernet won't go faster than 10 MByte per second.

Even so, if you get a decent sustained transfer rate of 15 MB per second it is still going to take 130 hours ( 5 1/2 days) to image 7 TeraBytes.

---

### Post by hal10000 on 2009-09-18
If you insist using dd, then you'll probably have to wait a week or so, but you also can use other (better) tools like [COLOR="Red"]partimage[/COLOR] or [COLOR="Red"]clonezilla[/COLOR] (which is a live-cd) and will be fine in between some hours.

[EDIT] You can do this only if you have hardware-raid

---

