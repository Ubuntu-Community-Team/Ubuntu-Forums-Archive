---
title: "Ubuntu Log from command line - Free Ram usage?"
date: 2011-08-22
forum: General Help
---

### Post by U2XS on 2011-08-22
Is it possible to narrow down the ram command to give me JUST the free ram?  Both commands that I know give me much more information that I would like to log.

```
free -m
```
This line gives me this.  I really only want the one under "free"

```
             total       used       free     shared    buffers     cached
Mem:          1262        612        649          0        250        114
-/+ buffers/cache:        247       1014
Swap:         4010          6       4003
```

```
cat /proc/meminfo
```
This line gives me this.  I really only want "MemFree"
```
MemTotal:      1292372 kB
MemFree:        636088 kB
Buffers:        279032 kB
Cached:         118768 kB
SwapCached:        532 kB
Active:         191408 kB
Inactive:       324684 kB
HighTotal:      392128 kB
HighFree:       188976 kB
LowTotal:       900244 kB
LowFree:        447112 kB
SwapTotal:     4106360 kB
SwapFree:      4099344 kB
Dirty:              40 kB
Writeback:           0 kB
AnonPages:      117756 kB
Mapped:          72072 kB
Slab:           102752 kB
SReclaimable:    80144 kB
SUnreclaim:      22608 kB
PageTables:       1660 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   4752544 kB
Committed_AS:   992956 kB
VmallocTotal:   110584 kB
VmallocUsed:     12020 kB
VmallocChunk:    95992 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     4096 kB
DirectMap4k:     12288 kB
DirectMap4M:    905216 kB
```

---

### Post by Wayne_V on 2011-08-22
one way: 

free -m | grep "^Mem:" | awk '{print $4}'

---

### Post by U2XS on 2011-08-22
> **Wayne_V said:**
> one way: 

free -m | grep "^Mem:" | awk '{print $4}'
Awesome, thanks!

---

