---
title: "ram"
date: 2011-03-12
forum: General Help
---

### Post by mmsmc on 2011-03-12
how do you check how much ram you have/are using

---

### Post by jerome1232 on 2011-03-12
Gui? System-Administration-System Monitor

cli, ```
free -m
```

Look at the -/+ Buffers line

---

### Post by rubylaser on 2011-03-12
From the terminal you can use these.

```
top | grep Mem
```
Use Ctrl+c to stop this, or do this...
```
cat /proc/meminfo
```

---

### Post by mmsmc on 2011-03-12
SwapTotal:       2437116 kB
SwapFree:        2437116 kB
Dirty:               252 kB
Writeback:             0 kB
AnonPages:        361240 kB
Mapped:            90560 kB
Shmem:             10256 kB
Slab:              25964 kB
SReclaimable:      14776 kB
SUnreclaim:        11188 kB
KernelStack:        2440 kB
PageTables:         6148 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2949384 kB
Committed_AS:    1364776 kB
VmallocTotal:     122880 kB
VmallocUsed:       17744 kB
VmallocChunk:      96820 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       12280 kB
DirectMap4M:      897024 kB


which one is RAM?

---

### Post by mmsmc on 2011-03-12
bump

---

### Post by Dlambert on 2011-03-12
> **mmsmc said:**
> bump

Swap is basically random access memory, but what does the system monitor say? For example on My pc it says 3.9 Gb for 4 gigs for ram.

---

### Post by uRock on 2011-03-12
Use htop in the terminal. It shows colorful RAM and CPU usage.

---

### Post by mmsmc on 2011-03-12
thanks!

---

