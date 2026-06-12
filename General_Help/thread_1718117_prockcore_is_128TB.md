---
title: "/proc/kcore is 128TB"
date: 2011-03-30
forum: General Help
---

### Post by okhowaboutthisusername on 2011-03-30
$ uname -a
Linux apollo 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

$ ls -l /proc/kcore 
-r-------- 1 root root 140737486266368 2011-03-30 21:19 /proc/kcore

$ ls -lh /proc/kcore 
-r-------- 1 root root 128T 2011-03-30 21:19 /proc/kcore

What's up with that? I realise it's just a virtual image (or something like that) but why so large? I *wish* I had 128TB of RAM.

$ cat /proc/meminfo 
MemTotal:        1506096 kB
MemFree:          472068 kB
Buffers:           31752 kB
Cached:           226348 kB
SwapCached:         3604 kB
Active:           546960 kB
Inactive:         375280 kB
Active(anon):     438316 kB
Inactive(anon):   239296 kB
Active(file):     108644 kB
Inactive(file):   135984 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       1461908 kB
SwapFree:        1436948 kB
Dirty:                72 kB
Writeback:             0 kB
AnonPages:        661300 kB
Mapped:           101740 kB
Shmem:             13472 kB
Slab:              40488 kB
SReclaimable:      24044 kB
SUnreclaim:        16444 kB
KernelStack:        2632 kB
PageTables:        26432 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2214956 kB
Committed_AS:    2091172 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       11576 kB
VmallocChunk:   34359723480 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:        9920 kB
DirectMap2M:     1529856 kB

---

