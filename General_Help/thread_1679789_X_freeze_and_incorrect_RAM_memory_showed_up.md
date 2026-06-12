---
title: "X freeze and incorrect RAM memory showed up"
date: 2011-02-01
forum: General Help
---

### Post by leviathan8 on 2011-02-01
Hi. I currently have installed 2 GiB RAM memory on a Dell laptop with Ubuntu 10.04 release. Today, as I was playing kmahjongg, suddenly my whole screen became black with a small " _ " symbol in the top left corner. My cursor showed up, however I wasn't able to use it. Inputing something with keyboard or trying to enter in tty didn't worked, so I restarted the machine with the power button. Now, when I check the gnome-system-monitor, it shows up that I have 1,8 GiB RAM memory available, instead of 1,9 GiB how it used to be. Any ideas?

---

### Post by leviathan8 on 2011-02-02
Regarding the ram issue, I think I pretty much found out where the problem is.

The memtotal is alright, but you see, the data buffers, as far as I know, use abnormally too much RAM.

```
mono@mono-laptop:~$ cat /proc/meminfo
MemTotal:        1923168 kB
MemFree:         1310680 kB
Buffers:           89424 kB
Cached:           287312 kB
SwapCached:            0 kB
Active:           224628 kB
Inactive:         322732 kB
Active(anon):     180316 kB
Inactive(anon):    71864 kB
Active(file):      44312 kB
Inactive(file):   250868 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1047640 kB
HighFree:         575608 kB
LowTotal:         875528 kB
LowFree:          735072 kB
SwapTotal:       1952760 kB
SwapFree:        1952760 kB
Dirty:                 8 kB
Writeback:             0 kB
AnonPages:        170632 kB
Mapped:            64228 kB
Shmem:             81556 kB
Slab:              21932 kB
SReclaimable:      11332 kB
SUnreclaim:        10600 kB
KernelStack:        2184 kB
PageTables:         4468 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2914344 kB
Committed_AS:     755148 kB
VmallocTotal:     122880 kB
VmallocUsed:       34748 kB
VmallocChunk:      37884 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB

```

Same with free:

```
mono@mono-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1878        628       1249          0         87        312
-/+ buffers/cache:        228       1649
Swap:         1906          0       1906

```

Is it normal that the data buffers use up to 87 mb ram?

---

