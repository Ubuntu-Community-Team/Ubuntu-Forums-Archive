---
title: "Ubuntu 10.10 suddenly freezing"
date: 2010-12-13
forum: General Help
---

### Post by Eng.AbuWleeD on 2010-12-13
Hi -

I have had problems for some time with my laptop suddenly freezing up  in graphical user mode. There does not seem to be any pattern to it, it will just suddenly freeze. Nothing will work.
When it freezes, I can't do ANYTHING.
Move the mouse, nothing.
Press a key, nothing.
Press a combination of keys, nothing.
Press and hold power button, laptop shuts off, I can restart it and proceed until the next time it freezes.
but I noticed that this problem occur just when I use the 3G modem (broadband) -Connect to Internet through ppp0-.
I have Ubuntu 10.10
but this problem doesn't occure in windows never so it is not a hardware problem(I think so).
this occurred in average once per week not frequently. 


/proc/[I]cpuinfo
[/I]```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping    : 6
cpu MHz        : 800.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts tpr_shadow vnmi flexpriority
bogomips    : 5053.63
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping    : 6
cpu MHz        : 800.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts tpr_shadow vnmi flexpriority
bogomips    : 5053.96
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

/proc/meminfo
```
abulwleed@Bilal-Pc:~$ cat /proc/meminfo
MemTotal:        2959912 kB
MemFree:         2170536 kB
Buffers:          139496 kB
Cached:           296292 kB
SwapCached:            0 kB
Active:           399164 kB
Inactive:         310636 kB
Active(anon):     274636 kB
Inactive(anon):    56672 kB
Active(file):     124528 kB
Inactive(file):   253964 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       2098444 kB
HighFree:        1513288 kB
LowTotal:         861468 kB
LowFree:          657248 kB
SwapTotal:       7999484 kB
SwapFree:        7999484 kB
Dirty:               140 kB
Writeback:             0 kB
AnonPages:        273904 kB
Mapped:            84536 kB
Shmem:             57300 kB
Slab:              35720 kB
SReclaimable:      19408 kB
SUnreclaim:        16312 kB
KernelStack:        2520 kB
PageTables:         5976 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     9479440 kB
Committed_AS:    1317532 kB
VmallocTotal:     122880 kB
VmallocUsed:       35172 kB
VmallocChunk:      69236 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB
```

Any ideas as to why this could be happening, and what I can do about it?
Thanks

---

### Post by Eng.AbuWleeD on 2010-12-15
!!! What is the problem with you guys ???
this is the must powerful forum in Ubuntu OS and here is the Giants of OS's



2 days left and no replay!!!

---

### Post by sikander3786 on 2010-12-15
I don't know why you didn't get any replies lately :-)

Most likely, a graphics problem. Which graphics card is there? Did you install the proprietary drivers (if available)?

```
lspci | grep VGA
```

Is compiz enabled?

For possible issues and troubleshooting with X freezes,

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by BiggoCharley on 2010-12-15
check this thread --massive problem
<http://ubuntuforums.org/showthread.php?t=1478787&highlight=freeze>

---

### Post by Eng.AbuWleeD on 2010-12-16
> **sikander3786 said:**
> I don't know why you didn't get any replies lately :-)

Most likely, a graphics problem. Which graphics card is there? Did you install the proprietary drivers (if available)?

```
lspci | grep VGA
```Is compiz enabled?

For possible issues and troubleshooting with X freezes,

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)


Thanks for replay 
lspci | grep VGA:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

yes compiz enables
do you think that compiz is the reason of freezing?
in its rational idea 
I will look in the link above,Thank you.

---

### Post by sikander3786 on 2010-12-17
Compiz as well your Intel Mobile graphics chipset might be responsible for the freeze. You can disable compiz for the moment and see if it still freezes. Or follow the wiki page above.

Let us know about your progress :-)

Good Luck!

---

### Post by azertyh on 2010-12-17
hello,
and look in your logs, sometimes there are error messages. in a terminal :
```
tail -f /var/log/syslog
```
and
```
dmesg
```

---

### Post by rainbowagent7 on 2011-02-05
!!!

---

