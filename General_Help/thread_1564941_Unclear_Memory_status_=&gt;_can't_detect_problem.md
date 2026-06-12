---
title: "Unclear Memory status =&gt; can't detect problem"
date: 2010-08-31
forum: General Help
---

### Post by seppl82 on 2010-08-31
Hi all,

currently i have a strange behavior according my memory.
Running Ubuntu 10.4 LTS Server 64 Bit

If i run mem

free -m
         ```
    total       used       free     shared    buffers     cached
Mem:          5965       5570        395          0         90       4738
-/+ buffers/cache:        740       5225
Swap:         9691        572       9119
```

But if i run the Gnome systgem monitor i'll see a memory ussage of only about 700 Megabytes. Which is absolutely strange.

For further analysis here is a output of 
cat /proc/meminfo

```
MemTotal:        6109100 kB
MemFree:          403124 kB
Buffers:           92972 kB
Cached:          4858780 kB
SwapCached:        67332 kB
Active:          1472536 kB
Inactive:        3775364 kB
Active(anon):     171628 kB
Inactive(anon):   137936 kB
Active(file):    1300908 kB
Inactive(file):  3637428 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       9924600 kB
SwapFree:        9338300 kB
Dirty:              2052 kB
Writeback:             0 kB
AnonPages:        260488 kB
Mapped:           383292 kB
Shmem:             13392 kB
Slab:             162352 kB
SReclaimable:     134740 kB
SUnreclaim:        27612 kB
KernelStack:        4512 kB
PageTables:        45628 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    12979148 kB
Committed_AS:    2660888 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      104820 kB
VmallocChunk:   34359629252 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:        7828 kB
DirectMap2M:     6266880 kB
```

---

