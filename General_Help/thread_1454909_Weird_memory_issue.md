---
title: "Weird memory issue"
date: 2010-04-15
forum: General Help
---

### Post by yeeeev on 2010-04-15
Hi,
 I have a very weird memory issue (as you may have guessed from the title :) ). There's a discrepency between the memory accumulated by the various applications (using "ps -eF" to collect that) and the memory reported by system monitor/"free"
Basically, I have around 0.5GB of memory that is not occupied by any application, but is not free as well. (It is not used as cache as well)
I restarted X (logged out and in again), but it didn't help.

free's output:
```

             total       used       free     shared    buffers     cached
Mem:       4056964    2874328    1182636          0     481360     592220
-/+ buffers/cache:    1800748    2256216
Swap:      6723160      31412    6691748

```
and on the other hand:
```

$ ps -eF | grep -v COMMAND | awk '{rsum+=$6}END{print rsum}'
1309016

```

I'm running Ubuntu 9.10 64bit.
I had some zombie processes, but I killed their parent process and that made them go away (and freed up some memory, but not all that's missing)
Any ideas how to further debug this would be appreciated.

Thanks!

---

### Post by yeeeev on 2010-04-16
OK, OK, it is cache... Just a rather peculiar one I wasn't aware of. I thought this issue might be related to a kernel memory leak, which led me to run slabtop. There I saw that "ext4_inode_cache" is just about the size of RAM I'm missing. (700MB)
I ran "sync; echo 3 > /proc/sys/vm/drop_caches" and that cleared everything right up... The funny thing is that the slab memory is not reported in system monitor/free as cached memory, but rather as used.

---

