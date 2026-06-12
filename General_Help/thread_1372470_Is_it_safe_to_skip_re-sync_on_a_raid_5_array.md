---
title: "Is it safe to skip re-sync on a raid 5 array?"
date: 2010-01-04
forum: General Help
---

### Post by jkounis on 2010-01-04
I took advantage of the long holiday weekend to install a new multi-terabyte RAID 5 array on our office server. Someday, the filesystem will hold our image library, but for now it is empty. 

There is no important data other than the superblocks and inode tables initially written by the mkfs.ext4 command.

When I created the raid array with mdadm, it started a long and process of resyncing the array. Now it's Monday, everyone is getting back to work, but the resync looks like it will last a couple more days. The load average on the server is still running 10-11, which negatively impacts our local web server, database server, email, and just about everything else.

My question is: 

Since there are only a few KB of useful data on the multi-TB volume, why do I have to resync the entire, empty volume before it is considered "clean" by mdadm? Is there any way to skip the resync of the empty data areas? Is it a smart thing to do?

---

### Post by Seq on 2010-01-04
> **jkounis said:**
> Since there are only a few KB of useful data on the multi-TB volume, why do I have to resync the entire, empty volume before it is considered "clean" by mdadm? Is there any way to skip the resync of the empty data areas? Is it a smart thing to do?

Probably because the MD layer doesn't know it is syncing empty data, just like ext4 doesn't really know it is on a 'Multiple Device' volume.

I'd just let it finish. You're going to have to let it some time anyway. Furthermore, rebuilding an array after a future disk failure will exert the same load on the system as well, and you can't skip those.

---

### Post by jkounis on 2010-01-04
Since it looks like the best course of action is to wait until the re-sync completes sometime Wednesday, I just used the following commands to try to improve the response for the rest of the users (where PID is the ID of the resync process md0_resync):

```
 sudo renice +5 -p <pid>
 sudo ionice -c3 -p<pid>
```

The effect is not as pronounced as I had hoped. The system is still very slow and load average is hovering in the high 10s/low 11s. I just wish there were a way to do this with less impact on the running system (like suspend the task during the day and continue it at night).

---

### Post by sdwood on 2010-01-14
> Is there any way to skip the resync of the empty data areas?Not the first time around.  To improve the performance of future rebuilds, however, you might consider adding a write-intent log to the array.   There will be performance implications, so you may wish to test throughput in your particular application.

[FONT=Courier New]mdadm --grow --bitmap=internal /dev/mdN[/FONT]

You can read more about *bitmap write-intent logging* in [FONT=Courier New]man 4 md[/FONT].

> I just wish there were a way to do this with less impact on the running system (like suspend the task during the day and continue it at night). 
Have you had any success by lowering [FONT=Courier New]/proc/sys/dev/raid/speed_limit_max?
[/FONT]

---

