---
title: "3 Gb Ram on a 4 Gb Box"
date: 2009-07-27
forum: General Help
---

### Post by Daniel.Ribeiro on 2009-07-27
Hi,

My ubuntu 9.04 (32 bit) only sees  3GB of my 4Gb ram. Searching around, I've heard that it might be that CONFIG_HIGHMEM64G is not set on my kernel. If this is the case, how do enable it? Are there other alternatives options for this problem? 

Stats:

```

root@fnord ~ # cat /boot/config-2.6.28-11-generic  |grep CONFIG_HIGHMEM
CONFIG_HIGHMEM=y
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set

```

```

root@fnord ~ # cat /proc/meminfo 
MemTotal:        3095220 kB
MemFree:         2509652 kB
Buffers:           16868 kB
Cached:           243096 kB
SwapCached:            0 kB
Active:           346072 kB
Inactive:         155132 kB
Active(anon):     246644 kB
Inactive(anon):        8 kB
Active(file):      99428 kB
Inactive(file):   155124 kB
Unevictable:           8 kB
Mlocked:               8 kB
HighTotal:       2238832 kB
HighFree:        1708248 kB
LowTotal:         856388 kB
LowFree:          801404 kB
SwapTotal:       8000328 kB
SwapFree:        8000328 kB
Dirty:                76 kB
Writeback:             0 kB
AnonPages:        241264 kB
Mapped:            68484 kB
Slab:              16312 kB
SReclaimable:       8452 kB
SUnreclaim:         7860 kB
PageTables:         2428 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     9547936 kB
Committed_AS:     527608 kB
VmallocTotal:     122880 kB
VmallocUsed:       24920 kB
VmallocChunk:      97364 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       12280 kB
DirectMap4M:      892928 kB

```

```

root@fnord ~ # free -m
             total       used       free     shared    buffers     cached
Mem:          3022        572       2450          0         16        237
-/+ buffers/cache:        318       2704
Swap:         7812          0       7812

```

---

### Post by t4thfavor on 2009-07-27
I have a 64 bit Intel GMA laptop who will only see 3GB in the os even though 4GB is detected at post. Its just a crappy chipset limitation. It even tests under Vista x64 as 4GB, under the system properties, and 3GB in dxdiag. SO go figure, its the hardware manufacturers using buzzwords, and not actually delivering a better product. 


If this was a HIGHMEM limit I believe you would see 3.5GB instead of 3, as the 3GB seems to be a chipset limit.

I have 32Bit boxes that have a full 4GB ram in them detected in the OS and everything.

---

### Post by Daniel.Ribeiro on 2009-07-27
But if I enable highmem, and it still doesn't show more than 3 GB of memory, than is it definitely the chipset problem? I just want to be more certain before hunting Dell down.

---

