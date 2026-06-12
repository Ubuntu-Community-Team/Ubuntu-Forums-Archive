---
title: "How to get rid of LVM formatting on Hard Drive?"
date: 2012-06-15
forum: General Help
---

### Post by held7over on 2012-06-15
Ubuntu 12.04

How do I wipe my hard drive?

I was playing with trying to set up LVM2 on a Hard Drive with fdisk, following a Ubuntu HowTo and made a mistake. The Hard Drive doesn't boot now and just has a blinking cursor on boot. I tried to use gparted to just erase my LVM2 scheme on the Drive, so I could start over, but even though gparted claims everything has been reduced to unallocated, or upon a different try, formatted to ext4 as one big partition, or I have used the LiveCD to repartition to a standard partition scheme that is then formatted and Ubuntu 12.04 written to it, apparently, this isn't the case...and the original LVM2 layout is still somehow present....messing up any new attempt I try to do...

Thanks!  :p

---

### Post by steeldriver on 2012-06-15
pvremove ?

[http://manpages.ubuntu.com/manpages/hardy/man8/pvremove.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pvremove.8.html)

if it's the last/only physical volume and you have actual volume groups and logical volumes on top you may need to break it down from the top (lvremove -> vgremove -> pvremove)

---

### Post by held7over on 2012-06-22
Sorry about the long pause....I ended up having to leave for a trip. I just got back.

lvremove, vgromove, and last, pvremove, worked great! I was then able to follow the instructions I had found for accomplishing what I wanted to do, and that worked also! Thanks!

I had thought gparted operated on a more fundamental level and was surprised I couldn't just wipe things out with it. I was thinking something was horribly wrong...

Your suggestion put me back on the right track. Thanks!

---

