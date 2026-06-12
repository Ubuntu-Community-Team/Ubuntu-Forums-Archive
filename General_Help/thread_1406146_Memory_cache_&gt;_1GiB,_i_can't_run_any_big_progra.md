---
title: "Memory cache &gt; 1GiB, i can't run any big programs"
date: 2010-02-13
forum: General Help
---

### Post by skynet1248 on 2010-02-13
This is my first post, so Hi Everybody

```
root@skynet-desktop:/proc# uname -r -m
2.6.31-19-generic x86_64

root@skynet-desktop:/proc# swapoff -a

root@skynet-desktop:/proc# free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1561        447          0          1       1045
-/+ buffers/cache:        514       1494
Swap:            0          0          0

root@skynet-desktop:/proc# cat meminfo 
MemTotal:        2056760 kB
MemFree:          449624 kB
Buffers:            5060 kB
Cached:          1075552 kB
SwapCached:            0 kB
Active:           193572 kB
Inactive:        1295324 kB
Active(anon):     185732 kB
Inactive(anon):  1252772 kB
Active(file):       7840 kB
Inactive(file):    42552 kB
Unevictable:          16 kB
Mlocked:              16 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                32 kB
Writeback:             0 kB
AnonPages:        408300 kB
Mapped:            42228 kB
Slab:              30760 kB
SReclaimable:      12924 kB
SUnreclaim:        17836 kB
PageTables:        16112 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1028380 kB
Committed_AS:    1875140 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      305476 kB
VmallocChunk:   34359414267 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      248704 kB
DirectMap2M:     1847296 kB

```

My ubuntu uses 514 MB, but cached memory takes 1GB+ memory, if i have swap on and if free memory < 5MB, kernel don't start drop cached memory, just uses swap for a program memory, that mean program run horrible slow.

I try
```
# echo 3 > /proc/sys/vm/drop_caches

```but only drop buffers, not cached memory

Is there a some reason why cached memory have this huge size?
Is possible to change size of cached memory or drop cached memory.

On 9.04 i could run eclipse and VBox[768MB uses] and i have 300MiB ram free, 0% swap use, now i can't run eclipse but begins using swap, and can't be usable.

ps. sorry for my poor English

---

### Post by rnerwein on 2010-02-13
hi
it's not 9.10 - i tried just now your command: echo 3 > /proc/sys/vm/drop_caches - and the caches ( pagecaches and dentries) where droped.
must have another reason. i guess that VBox is locking his memory.
or have a look at your vm.swappiness = ?, vm.dirty_ratio = ? and vm.dirty_background_ratio 
(see manpages: man proc )
ciao

---

### Post by falconindy on 2010-02-13
The output of 'free' is very misleading. What you have missed is that the second line...
```
-/+ buffers/cache:        514       1494
```
Is actually telling you exactly how much you have free -- the 1494mb is what you have available after discounting the 514mb  claimed by buffers and caches. It's inaccurate in that it's not really in use. This memory will be immediately given up to any program requesting it, should it be warranted.

If you're **actually** running into a situation where you're exhausting your RAM, you need to create a swap partition, or swap file.

---

### Post by skynet1248 on 2010-02-13
> **rnerwein said:**
> or have a look at your vm.swappiness = ?, vm.dirty_ratio = ? and vm.dirty_background_ratio 

It's Ubuntu 9.10 x64, i try change /proc/sys/vm/* files but cacheed memory can't go to swap or "/dev/null"

```
skynet@skynet-desktop:~$ cat /etc/apt/sources.list | grep cdrom
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted

```


```
/proc/sys/vm/block_dump, 0
/proc/sys/vm/dirty_background_bytes, 0
/proc/sys/vm/dirty_background_ratio, 10
/proc/sys/vm/dirty_bytes, 0
/proc/sys/vm/dirty_expire_centisecs, 3000
/proc/sys/vm/dirty_ratio, 20
/proc/sys/vm/dirty_writeback_centisecs, 500
/proc/sys/vm/drop_caches, 3
/proc/sys/vm/hugepages_treat_as_movable, 0
/proc/sys/vm/hugetlb_shm_group, 0
/proc/sys/vm/laptop_mode, 0
/proc/sys/vm/legacy_va_layout, 0
/proc/sys/vm/lowmem_reserve_ratio, 256 256 32
/proc/sys/vm/max_map_count, 65530
/proc/sys/vm/min_free_kbytes, 5750
/proc/sys/vm/min_slab_ratio, 5
/proc/sys/vm/min_unmapped_ratio, 1
/proc/sys/vm/mmap_min_addr, 0
/proc/sys/vm/nr_hugepages, 0
/proc/sys/vm/nr_overcommit_hugepages, 0
/proc/sys/vm/nr_pdflush_threads, 2
/proc/sys/vm/numa_zonelist_order, default
/proc/sys/vm/oom_dump_tasks, 0
/proc/sys/vm/oom_kill_allocating_task, 0
/proc/sys/vm/overcommit_memory, 0
/proc/sys/vm/overcommit_ratio, 50
/proc/sys/vm/page-cluster, 3
/proc/sys/vm/panic_on_oom, 0
/proc/sys/vm/percpu_pagelist_fraction, 0
/proc/sys/vm/scan_unevictable_pages, 0
/proc/sys/vm/stat_interval, 1
/proc/sys/vm/swappiness, 60
/proc/sys/vm/vfs_cache_pressure, 100
/proc/sys/vm/zone_reclaim_mode, 0
```

**falconindy** I have 4 GB swap memory, but cached mem forces use a swap for the program memory, why cached mem don't go to swap?

SOLVED
```
# apt-get install ureadahead sreadahead

```and```

# echo 3 > /proc/sys/vm/drop_caches
```
works !

and cached mem goto swap if free mem < 5

---

### Post by falconindy on 2010-02-13
Mmmm, I should read more closely next time. Skipped over the line where you disabled your swap. I still think you're changing behavior you don't fully understand.

---

### Post by skynet1248 on 2010-02-13
> **falconindy said:**
> Mmmm, I should read more closely next time. Skipped over the line where you disabled your swap. I still think you're changing behavior you don't fully understand.

Probably you have right, I not fully understand how works cache in linux system.

Now i run VBox and
```
root@skynet-desktop:/home/skynet# free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1993         15          0         10        340
-/+ buffers/cache:       1642        366
Swap:         4094         17       4077
```

As you see cached memory are dropped from 1GB to 340 MB, i think this:
ureadahead control system cache memory behavior

---

