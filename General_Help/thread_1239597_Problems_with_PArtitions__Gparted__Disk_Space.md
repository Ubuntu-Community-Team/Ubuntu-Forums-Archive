---
title: "Problems with PArtitions / Gparted / Disk Space"
date: 2009-08-13
forum: General Help
---

### Post by krimzen85 on 2009-08-13
Hey All,

So I've got Linux online and operational, finally. I went to do 
sudo apt-get update, and the update manager came up, requesting to 
install about 350mg of updates onto my system.  I went to accept and
it told me that there isn't enough disk space, and to free up 292mb
of space.

I did:

sudo apt-get install gparted
sudo gparted

What this shows me, is that my mount point (/) is running on
/dev/sda5 (ext3), which has a total size of 2.33g.  Right now, I 
am utilizing 2.12g of space, leaving about 209mb free.  Easy enough,
makes sense.

Here's the thing though:

I can see on this list of partitions, that /dev/sda1 (nfts) has 132g
of space, and none of it is used, because the current active 
partition is /dev/sda5, which is only 2.33g.

So, assuming that this is the problem, how do I migrate the 2.12g
of data over to the partition with 132g of space, and make that the
active partition, so I can install these updates?

---

### Post by michy99 on 2009-08-13
All the answers shall be revealed in this thread:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

