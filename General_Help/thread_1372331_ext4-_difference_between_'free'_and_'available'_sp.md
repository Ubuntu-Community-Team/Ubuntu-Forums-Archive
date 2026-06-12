---
title: "ext4- difference between 'free' and 'available' space"
date: 2010-01-04
forum: General Help
---

### Post by Megarock on 2010-01-04
according to the system manager of my machine, one of my ext4 partitions (home folder) reads 7.6GB free but only 574MB available and the disks "fills" when the 574MB are used, and i'm really needing those 7G right now, so:

why does this happen? are those 7G used in *any*thing?
any way to allow the system use that free space?

---

### Post by warfacegod on 2010-01-04
At a guess, I'd say those 7GB are reserved by the system.


Try using *sudo tune2fs* in the terminal. I can't remember the exact command so look for it in the forum. Be certain you use it on the right partition or drive.


Nice avatar. My best friend is a Maiden fan. It's SLAYER for me.

---

### Post by Megarock on 2010-01-04
ok, so read a bit on the net and found this:
```
tune2fs -m <percent of reserved blocks> <device>
```
is it safe to reduce it to, say, 0% considering its the home folder? what is important to consider when setting the reserved blocks number?

off-topic:
slayer is definitely my second to best band before maiden :mrgreen:. on their earlier works, the newer are meh-ish; not bad, but meh

---

### Post by mcduck on 2010-01-04
Is it a home directory, or a home partition?

5% of disk space on Ext filesystems is reserved for root user only, since the system needs some disk space to work correctly. Reserving this space makes sure that normal users can't accidentally fill the drive to the point where the system wouldn't be able to boot any more.

You definitely want to keep this reserved space on your root partition, for any other partitions it's safe to set the limit to 0. If you have a very large root partition then something less than 5% would be enough (Gigabyte or two should be more than enough), but you really don't want to do that anyway since the performance of Ext filesystems starts to decrease rapidly when the drive gets too full. So you really wouldn't want to fill any Ext partition over 90% anyway, at least as long as you have any other options.

---

### Post by warfacegod on 2010-01-04
> is it safe to reduce it to, say, 0% considering its the home folder? what is important to consider when setting the reserved blocks number?


Yes, assuming that the home folder is on a seperate partition. If it's not then using 0% will probably give you minor issues like cd burning may not work. I used 0% on my external and got back 40 something Gigs.

---

### Post by Megarock on 2010-01-04
yeah, the partition is only the home folder.

thx for the replies

---

### Post by doas777 on 2010-01-04
how heavy is your lost and found, and have you emptied the trash?

---

### Post by Megarock on 2010-01-04
> **doas777 said:**
> how heavy is your lost and found, and have you emptied the trash?
yeah, checked that before trying this, both empty :P

---

### Post by warfacegod on 2010-01-04
daos777 has an excellent point. Try searching the forums for that and other ways to clean up.


> yeah, the partition is only the home folder.


Then, by all means, go with 0%.

---

### Post by anaconda on 2010-01-04
the 5% reserved for root is ridiculously much these days..

100MB would be more than enough for the purpose, so you can safely resuce it to 1% for root partition and 0% for home partition

---

### Post by warfacegod on 2010-01-04
> **anaconda said:**
> the 5% reserved for root is ridiculously much these days..

100MB would be more than enough for the purpose, so you can safely resuce it to 1% for root partition and 0% for home partition

Only 100MB seems to be a bit extreme. 1 GB would be far more reasonable. Say you stream a movie from netflix, it would go to the tmp folder, 100MB would be gone in a flash. Burning a dvd would be the same thing. It would only have 100MB for a checksum and the process would slow to crawl virtually guarranteeing write errors.

---

### Post by bodhi.zazen on 2010-01-04
> **anaconda said:**
> the 5% reserved for root is ridiculously much these days..

100mb would be more than enough for the purpose, so you can safely resuce it to 1% for root partition and 0% for home partition

+1

---

### Post by anaconda on 2010-01-05
> **warfacegod said:**
> Only 100MB seems to be a bit extreme. 1 GB would be far more reasonable. Say you stream a movie from netflix, it would go to the tmp folder, 100MB would be gone in a flash. Burning a dvd would be the same thing. It would only have 100MB for a checksum and the process would slow to crawl virtually guarranteeing write errors.

the space reserved for root user (5% or preferably 100MB) is not used for streaming movies, or burning DVD:s. Only root user can use it, and it becomes necessary only when normal user has used all available space he can use. (and normal user cant boot any longer, because the disk is full)

Then you can boot to recovery mode (as root) and you will have 100MB room (or whatever amount reserved for root) and you can correct the problem. eg. by deleting unnecessary data or moving it to USB-drive or whatever. 

For this purpose 100MB is more than enough. 

(OK. if you want to free some space by burning DVD:s, then you might need more... didn't think of that)

PS: the 5% default setting is ancient.. it was good when the harddisk sizes were in the range of 100MB-2GB... Amazing that no-one has changed the default to a fixed amout yet.. the 5% from a 2TB disk is just nuts..

---

