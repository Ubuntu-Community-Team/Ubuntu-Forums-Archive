---
title: "Why does Ubuntu 11.04 show that I have 2.9GB of RAM when I have 4GB?"
date: 2011-07-22
forum: General Help
---

### Post by ImageJPEG on 2011-07-22
I am running a 64 bit OS.

**Linux Sapphire 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux**

[B]total       used       free     shared    buffers     cached
Mem:          3016        945       2071          0         53        372
-/+ buffers/cache:        519       2497
Swap:          486          0        486[/B]

I have installed 4GB so what's going on?

---

### Post by altometer on 2011-07-22
Can you provide the output of
```
uname -m
```

---

### Post by spcwingo on 2011-07-22
Are you using an integrated video card...possibly with 1 GB of shared RAM?

---

### Post by sikander3786 on 2011-07-22
Can you please take a look in your Bios setup and see how much RAM is initially being detected there? If the Bios also detects 3GB of RAM, perhaps there is a hardware problem.

The 64-bit Kernel should detect 4GB RAM and the output tells that you are running 64-bit.

---

### Post by ImageJPEG on 2011-07-26
The BIOS detects all 4 1GB slots. My motherboard does support up to 4GB of RAM. My video card is an Nvidia 8600GT with (I think 256MB VRAM) and I'm not giving any of my RAM to the video card. I just reinstalled Ubuntu so I'll see if that fixes the problem.

---

### Post by Wayne_V on 2011-07-26
cat /proc/{meminfo,cmdline}

---

### Post by ImageJPEG on 2011-07-26
[B]MemTotal:        3088948 kB
MemFree:         2133124 kB
Buffers:           41600 kB
Cached:           463732 kB
SwapCached:            0 kB
Active:           428584 kB
Inactive:         365020 kB
Active(anon):     289008 kB
Inactive(anon):     2872 kB
Active(file):     139576 kB
Inactive(file):   362148 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:        498684 kB
SwapFree:         498684 kB
Dirty:              1392 kB
Writeback:             0 kB
AnonPages:        288192 kB
Mapped:           107148 kB
Shmem:              3612 kB
Slab:              47876 kB
SReclaimable:      30488 kB
SUnreclaim:        17388 kB
KernelStack:        2384 kB
PageTables:        19716 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2043156 kB
Committed_AS:    1529600 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      321592 kB
VmallocChunk:   34359405564 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       62000 kB
DirectMap2M:     3082240 kB[/B]

---

### Post by holadebob on 2011-07-26
Had similar problem, have Gigabyte MB. Gigabyte specs say 4GB max, but only showed a bit more than 3GB. I asked Gigabyte what gives, and they said the chipset wouldn't address 4GB. I checked the specs on the chipset, Intel, and seemed to be true. Gigabyte says they made provisions for two 2GB ram sticks, but didn't say they couldn't use them. True the video takes some, but only a couple of MB. Don't know if this is your problem also, but you might check it out.

---

### Post by Wayne_V on 2011-07-27
unless your boot cmdline (cat /proc/cmdline) has the memory limited (see pg 93 here: [http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf](http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf))  I would guess it is a BIOS issue.  Have you checked your MB manufacture for updates or known bugs?

---

### Post by Gyokuro on 2011-07-27
Which motherboard are you using? Look in your BIOS for something like memory remapping and activate it.

---

