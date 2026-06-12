---
title: "gparted - unallocated space"
date: 2011-03-20
forum: General Help
---

### Post by sssecure on 2011-03-20
Hello, is there any way how to merge all those unallocated partitions into one? 

[http://imghosting.byl.cz/images/screenkrk.png](http://imghosting.byl.cz/images/screenkrk.png)

my sys is ubuntu 10.04 LTS x64

---

### Post by Quackers on 2011-03-20
Not really. You could extend the partition right next to each one, but to be honest, 100MB and 210MB is not a lot to lose.

---

### Post by sssecure on 2011-03-20
Okay, thank you. When i try to create a new partition from the unallocated spaces [1 space 1 partition], it says that there can't be more than 4 primary partitions, so i can't even create them as extended.

---

### Post by Quackers on 2011-03-20
Not if you've already got 4 primary partitions, no.
Even if you could, they would be very small partitions! :-)

---

### Post by srs5694 on 2011-03-20
Concerning the 4-partition limit, I suspect you've already got an extended partition, although the way it's labelled in your screen shot is a way I've never seen GParted label partitions. If I'm right, though, you should be able to move/resize your partitions to create whatever amount of free space you want, move that free space inside your extended partition (/dev/sda2 if I'm right, or "New Partition #1" in your screen shot), and create new logical partitions.

If that fails, you should be able to use my [FixParts](http://www.rodsbooks.com/fixparts/) program to juggle the primary/logical status of at least some of your partitions. That might give you the extra flexibility you need to accomplish whatever you hope to accomplish.

Another point is that it is possible to combine separated partitions into a single block of storage space by using LVM. This can get a bit hairy, though, and I agree with Quackers that 301 MiB just isn't enough free space to be bothering with. You might consider using this approach, perhaps combined with some other options to free up space, to add space while minimizing the amount of partition moving you've got to do, since moving partitions is inherently pretty dangerous. If you want to pursue this approach, you can read up about it in the [LVM HOWTO document,](http://tldp.org/HOWTO/LVM-HOWTO/) or Google it for more references (there are lots).

---

