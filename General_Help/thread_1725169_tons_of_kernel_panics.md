---
title: "tons of kernel panics"
date: 2011-04-09
forum: General Help
---

### Post by markolonius on 2011-04-09
Hello.  I've been experiencing kernel panics like crazy for quite a while now..  I don't know the exact cause of the panic. Seems to happen when the machine is idle.  I'm running ubuntu 10.10 server headless an all.  Below is some info about the machine that could help.  I've attached logs that I think might help as well as a picture of the screen after kernel panic all in a tar file.  Any help would be appreciated.


```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
```


```
$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: CentaurHauls
cpu family	: 6
model		: 10
model name	: VIA Esther processor 1500MHz
stepping	: 9
cpu MHz		: 1496.124
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx up pni rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en
bogomips	: 2992.24
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 32 bits virtual
power management:
```

```
$ cat /proc/meminfo 
MemTotal:        1994864 kB
MemFree:         1315688 kB
Buffers:           53812 kB
Cached:           546736 kB
SwapCached:            0 kB
Active:           236624 kB
Inactive:         400272 kB
Active(anon):      37048 kB
Inactive(anon):     2176 kB
Active(file):     199576 kB
Inactive(file):   398096 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1117128 kB
HighFree:         531600 kB
LowTotal:         877736 kB
LowFree:          784088 kB
SwapTotal:       5840892 kB
SwapFree:        5840892 kB
Dirty:                12 kB
Writeback:             0 kB
AnonPages:         36340 kB
Mapped:            22292 kB
Shmem:              2884 kB
Slab:              26948 kB
SReclaimable:      20156 kB
SUnreclaim:         6792 kB
KernelStack:        1352 kB
PageTables:         1148 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6838324 kB
Committed_AS:     324184 kB
VmallocTotal:     122880 kB
VmallocUsed:        4852 kB
VmallocChunk:     113888 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       12280 kB
DirectMap2M:      901120 kB
```


Any help would be appreciated..  I've been thinking to switch to freebsd to see if it still happens, but I feel like this problem can be fixed.  Worst case it is a hardware issue.  Let me know if you need any other information logs and such.  Thanks!

---

### Post by Hedgehog1 on 2011-04-09
> Hello. I've been experiencing kernel panics like crazy for quite a while now.. I don't know the exact cause of the panic. **Seems to happen when the machine is idle**. 

The first thing I would suspect that that your hard drives are spinning down when idle, and then the next attempt to access them after the snip down is creating and error rather then a delay while they spin back up.

For a server, I would not let the drives spin down.


T***he Hedge***

:KS

---

### Post by markolonius on 2011-04-09
Thanks for the quick reply!  That does make sense.  I'll try disabling spin down.  If that works i'll enable one hard drive to see which is causing possible error.  Any benchmarks or diagnostic i can run on my harddrives to see possible errors? i've done smartctl, which didn't show any error.

Thanks again!


Update:

So disabling spindown didn't seem to do the trick.  Any other ideas?  Any other way to get a hint?


update again:

seems to have something to do with the some clock... i saw 'clocksource tsc unstable' last line in the kernel.log.1  searching google seems to show i'd have to try a billion things to see if they work.  moving to bsd maybe

---

