---
title: "RAM usage issue (cached?..)"
date: 2009-12-22
forum: General Help
---

### Post by sunrex on 2009-12-22
Free is showing the following:

```
[root@firefly ~]# free
             total       used       free     shared    buffers     cached
Mem:       8048940    1509988    6538952          0     238848     908884
-/+ buffers/cache:     362256    7686684
Swap:            0          0          0

```

As you can see, apparently almost all my RAM (8GB) is sitting in cache.

There is no SWAP partition.

Can I limit the amount of RAM the system can shove in cache, or at least have something automatically clean it up every hour or so?.

Thanks for your help.

---

### Post by falconindy on 2009-12-22
Actually, **all** your RAM is in the cache. 

7686684 + 362256 = 8048940

This is normal operation. If you want to "limit" the amount of RAM going into the cache, you can physically remove it from the motherboard. (lol?)

---

### Post by Some Penguin on 2009-12-22
It'll free it for other purposes when you actually need the memory.

---

### Post by dcstar on 2009-12-22
> **sunrex said:**
> 
.........
Can I limit the amount of RAM the system can shove in cache, or at least have something automatically clean it up every hour or so?.


Pointless, the system will use the RAM when it needs it.

---

