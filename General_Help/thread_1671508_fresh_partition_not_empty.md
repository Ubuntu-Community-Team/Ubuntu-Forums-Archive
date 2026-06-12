---
title: "fresh partition not empty"
date: 2011-01-20
forum: General Help
---

### Post by getack on 2011-01-20
Hello friends

So the other day I got myself a nifty ThinkPad x100e. I immediately removed windows 7 started, and installed UNR 10.04.

It has a 250GB hard drive, which I decided to partition, so that I can keep all my stuff on the new partition, and then a fresh format or install of the OS would be easier.

After struggling to take ownership of my own damn partition after creating it and mounting it, I discovered a rather interesting problem. I KNOW the partition is empty, but when I right click and go to properties, it says that 10GB is already used? This is rather confusing to me. 

I formatted it to ext4.

Any ideas?

tl;dr: Freshly formatted ext4 partition showing 10GB already used.. Help?

---

### Post by yetiman64 on 2011-01-20
As a normal loss for ext4 can be as much as 5 % of total partition size. 10G loss for a partition of 200 G would be about normal. This space is used for the filesystem table of contents etc.

How big is the partition in question ?

---

### Post by bikodog on 2011-01-20
Think of it as "reserved" space for file information. The net effect is the same, 200G of data; but arranged in a very efficient way.

---

### Post by louieb on 2011-01-20
By default ext4 will reserve about 5% of a partitions space for critical system tasks. (Just in case space runs low the OS still has some disk space it can use).

The reserve space can be adjusted with tune2fs - personally I let the default stand.

---

### Post by getack on 2011-01-20
Thanks for the speedy responses. The partition is 200GB, so it must be the reserved space that's eating up my 10GB.

Second question. Will I be able to cram more stuff onto the partition if I reformat to a ext3/2 partition that does not reserve the space? The partition is purely for storage (music, docs etc), nothing else.

Thanks again all, this is the fastest I've ever been helped with a tech related problem, and it's free ;-)

---

### Post by getack on 2011-01-20
Thanks for the speedy responses. The partition is 200GB, so it must be the reserved space that's eating up my 10GB.

Second question. Will I be able to cram more stuff onto the partition if I reformat to a ext3/2 partition that does not reserve the space? The partition is purely for storage (music, docs etc), nothing else.

Thanks again all, this is the fastest I've ever been helped with a tech related problem, and it's free ;-)

---

### Post by louieb on 2011-01-21
> **getack said:**
> ... if I reformat to a ext3/2 partition that does not reserve the space? The partition is purely for storage (music, docs etc), nothing else....;-)

ext2/3 reserve space too. Your probably don't want reserve space set to zero. from **man tune2fs**
> 
-m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by privileged processes.   Reserving some number  of  filesystem
              blocks for use by privileged processes is done to avoid filesys-
              tem fragmentation, and to allow system  daemons,  such  as  sys-
              logd(8),  to continue to function correctly after non-privileged
              processes are prevented from writing to  the  filesystem.   Nor-
              mally, the default percentage of reserved blocks is 5%.

having reserve space help avoid file fragmentation and generally will allow faster disk access. 
But heres how.
```
tune2fs -m0 /dev/sdxx
```

---

### Post by baliganikhil on 2011-01-21
Some netbooks use around 10 GB space to hold a recovery disk. Normally, pressing F8 (could be something else) in the beginning takes you to recovery mode to recover your netbook (reinstall windows)

Of course, I know you say that you have formatted it, so it is most likely what the rest of them here are saying... This is just another angle

---

