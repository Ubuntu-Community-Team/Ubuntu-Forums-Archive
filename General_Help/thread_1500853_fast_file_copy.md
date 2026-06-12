---
title: "fast file copy?"
date: 2010-06-03
forum: General Help
---

### Post by UT8F on 2010-06-03
Is there any way, to make file copy operation faster? I mean, copyin file from one folder to another is very slow.

---

### Post by lsk3993 on 2010-06-03
> **UT8F said:**
> Is there any way, to make file copy operation faster? I mean, copyin file from one folder to another is very slow.
Someone else can correct me if I'm wrong but I'm pretty sure this is to do with your hard drive. If the write speed is slow then you can't really fix that without getting a new drive.

---

### Post by elliotn on 2010-06-03
True

---

### Post by Jeroensum on 2010-06-04
That's not entirely true guys... infact, it's dead wrong. ;o)

You can absotiveley tweak things regarding your drive. Take hdparm for starters, in a lot of cases you can improve the read speed of your drive and sometimes also the write speed.

Also you can improve performance by the way you mount your filesystem, for example, you could do without atime, by setting the noatime in the mount options. This will tell the filesystem not to write the accesstimes to each and everyfile it accesses, hence decreasing read/write activity which can then be used by other processes.

There is a nice tutorial on hdparm and how to set noatime to be found here:
[http://www.linux.com/archive/articles/116693](http://www.linux.com/archive/articles/116693)

Lastly your file system matters, alot even.
It's good practise to know what you're going to store and where. For example if you are going to store a whole bunch of photo's, which are generally small in size, then you would use a file system like reiser or ext3/4. On the other hand if you are going to store things like iso's or virtualbox machines on a partition, then you would go for xfs or jfs. For most /boot partitions often ext2 is used, since this fs doesn't use journaling and thus is a bit faster. The downside of no journal is that it's hard to recover but heck, it's only boot, you can restore it with a live cd in about 5 minutes :)

So, there might be a lot to tweak and finetune and squeeze a bit more performance out of that drive of yours!

---

