---
title: "Missing disc space"
date: 2012-01-26
forum: General Help
---

### Post by r1ba5 on 2012-01-26
Hey, I have another problem. The hdd is 320GB size, swap has 12GB, so that leaves 308.. See the pic.

This what I get in terminal:
```

:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             283G  268G  849M 100% /
none                  2,0G  332K  2,0G   1% /dev
none                  2,0G  120K  2,0G   1% /dev/shm
none                  2,0G   84K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
none                  283G  268G  849M 100% /var/lib/ureadahead/debugfs

```Any ideas?:confused:

---

### Post by Nixarter on 2012-01-26
File systems measure in binary gigabytes, and drive manufacturers measure in billions of bytes.  So a 320 gb hard drive has about 320,000,000,000 bytes.  Binary bytes are measured by powers starting with one binary kilobyte (which is 2^10, or 1024 bytes).  So, one binary mb = 1kb^2 = 1024*1024=1,048,576 bytes.  And one binary gb = 1kb^3=1024*1024*1024 = 1,073,741,824 bytes.  So, 320,000,000,000(320 billion bytes)/1,073,741,824 (1 binary gb) = (about) 298 binary gb.  298-12=286 binary gb free.

Depending on the program you used to format, it may have made it 15gb for swap instead of 12gb, which is where that missing 3gb could be.

---

### Post by r1ba5 on 2012-01-26
yeah, but it says: there is 283, I'm using 268 and that makes 100%? 283-268=15 - that's the problem

---

### Post by Cheesemill on 2012-01-26
By default 5% of the capacity of an ext volume is reserved for system use.
Would this be it?

For more info and how to change this behaviour:
[http://tombuntu.com/index.php/2009/03/11/free-disk-space-by-reducing-reserved-blocks/](http://tombuntu.com/index.php/2009/03/11/free-disk-space-by-reducing-reserved-blocks/)

---

### Post by mcduck on 2012-01-26
> **r1ba5 said:**
> yeah, but it says: there is 283, I'm using 268 and that makes 100%? 283-268=15 - that's the problem
5% of disk space on Ext filesystems is reserved for root user only, to prevent normal user's from filling the drive to the point where the system wouldn't be able to function any more (for example starting up Linux requires creating some files, so you must have certain amount of free drive space or you can't boot at all).

The amount of reserved space can be changed, but I wouldn't recommend doing that on your root partition. And on the other hand you might not want to do it on any other partition either, while Ext filesystems are pretty good at avoiding file fragmentation, it will happen when the drive gets too full. After around 90% of used space the performance will start decreasing quickly, so you wouldn't actually want to ever use all the space....

---

### Post by r1ba5 on 2012-01-26
Well, 5% makes for 14.15GB, so it might. But wouldn't these 5% be included in the 'used' space?
Is there a way to check it? And reduce the 5%? :)

-> Ok, thanks for the info :) Just 1 more thing: can I reduce the swap area and attach it to the main partition? I think 4GB would be enough for me

---

### Post by mcduck on 2012-01-26
> **r1ba5 said:**
> Well, 5% makes for 14.15GB, so it might. But wouldn't these 5% be included in the 'used' space?
Is there a way to check it? And reduce the 5%? :)

No, it's not included in "used" space as it's not used, it's free. And it's not included in "available" either, as it's not available for the user. :)

Like I said, you shouldn't change the reserved amount on your root partition, and in the end you really wouldn't even want to use that space for anything, but if you decide to go against this advice, then *tune2fs* is the command you are looking for...

---

### Post by sffvba[e0rt on 2012-01-27
*Thread moved to **General Help** and its own thread.*


404

---

### Post by sffvba[e0rt on 2012-01-27
> none                  283G  268G  849M 100% /var/lib/ureadahead/debugfs

This issue has come up before - [http://ubuntuforums.org/showthread.php?t=1350785&page=2](http://ubuntuforums.org/showthread.php?t=1350785&page=2)

And there is a bug - [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/499773)

Now I am not really understanding this but it seems to me that /var/lib/ureadahead/debugfs
 shouldn't be showing up but the fact that it does it just a bug, I don't think your root is really full.


404

---

