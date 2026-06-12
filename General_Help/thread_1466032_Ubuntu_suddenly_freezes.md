---
title: "Ubuntu suddenly freezes"
date: 2010-04-29
forum: General Help
---

### Post by topgun_tapan on 2010-04-29
I've a strange problem with my ubuntu 9.10 installation. Whenever i boot into ubuntu the entire system freezes / hangs soon after (~ 2 mins in). This problem exists on my windows 7 installation too. However if i start World of Warcraft or Warcraft on windows it doesnt hang for the duration i'm playing the game. After i stop playing and exit the game my laptop hangs inside 2 mins.
However when I start it in ubuntu recovery mode and drop to root shell and use the 'startx' command everything works perfectly. I cannot figure out what the problem is. I'm also kind of a noob in linux so please let me know what extra information you need and the commands i need to run to get that information.
Thanks in advance.

---

### Post by Crafty Kisses on 2010-04-30
Do you know your system specs?

---

### Post by topgun_tapan on 2010-04-30
yes of course .. here they are
i have an intel core2duo 2.2ghz processor
intel mobile 965 graphics
2 GB RAM

for more details here is the output of cat /proc/cpuinfo :
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping    : 11
cpu MHz        : 2201.000
cache size    : 4096 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips    : 4389.80
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping    : 11
cpu MHz        : 2201.000
cache size    : 4096 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips    : 4388.96
clflush size    : 64
power management:

```

here is the output of cat /proc/meminfo

```
MemTotal:        2052440 kB
MemFree:           55924 kB
Buffers:          579352 kB
Cached:           821752 kB
SwapCached:          704 kB
Active:           897124 kB
Inactive:        1032256 kB
Active(anon):     412140 kB
Inactive(anon):   264804 kB
Active(file):     484984 kB
Inactive(file):   767452 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1178440 kB
HighFree:           6012 kB
LowTotal:         874000 kB
LowFree:           49912 kB
SwapTotal:        995988 kB
SwapFree:         986616 kB
Dirty:              8928 kB
Writeback:             0 kB
AnonPages:        527596 kB
Mapped:            76536 kB
Slab:              39480 kB
SReclaimable:      21100 kB
SUnreclaim:        18380 kB
PageTables:         5672 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2022208 kB
Committed_AS:    1856400 kB
VmallocTotal:     122880 kB
VmallocUsed:       11928 kB
VmallocChunk:     104644 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB

```

---

### Post by topgun_tapan on 2010-05-04
^bump^ :confused:

---

### Post by Crafty Kisses on 2010-05-08
Hello,

Sorry it took me a couple of days to respond, as I have been busy with other projects, and I will try and help you out to the best of my ability. Ok so first, I need a couple of results of a couple of different thins, so I can just see some logs.

```
dmesg
cat /var/log/kern.log
```

Post those back here. Your initial system specs seem very solid and should be able to run an Ubuntu installation just fine. So let's see if we can't find the solution!

---

### Post by soltanis on 2010-05-08
Sounds like a hardware bug + a kernel panic. Does running other graphics/CPU intensive apps delay the problem? Perhaps if you run a GPU benchmark tool, does that help?

And yeah, we'll need as many kernel/system logs as can be scrounged.

---

### Post by topgun_tapan on 2010-05-11
Sorry for the late reply. Had stopped checking up on this thread :). I didnt know what exact part you wanted from the kern.log so i booted into my regular ubuntu and let it crash. Here is the part of the log from just before the crash to the next restart. I will also attach the entire log if you need to look through it. I cant exactly make out what went wrong here since the log shows no errors. In fact i had a friend who knows some stuff about linux look through the other logs as well like dmesg and some others. No errors there too. Its like everything just freezes.

```
May 11 12:15:23 tapan-laptop kernel: [   24.848494] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 11 12:15:23 tapan-laptop kernel: [   25.227700] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:23 tapan-laptop kernel: [   25.368624] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:24 tapan-laptop kernel: [   25.639821] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:24 tapan-laptop kernel: [   25.779764] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:29 tapan-laptop kernel: [   31.254733] ppdev: user-space parallel port driver
May 11 12:15:31 tapan-laptop kernel: [   32.376720] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:31 tapan-laptop kernel: [   32.518811] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:31 tapan-laptop kernel: [   32.797149] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:31 tapan-laptop kernel: [   32.937760] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:31 tapan-laptop kernel: [   33.284161] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:32 tapan-laptop kernel: [   33.426825] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:42 tapan-laptop kernel: [   43.986717] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:42 tapan-laptop kernel: [   44.129233] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:43 tapan-laptop kernel: [   44.402794] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:43 tapan-laptop kernel: [   44.543948] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:43 tapan-laptop kernel: [   44.811451] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:43 tapan-laptop kernel: [   44.951360] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:44 tapan-laptop kernel: [   46.278561] [drm] TV-14: set mode NTSC 480i 0
May 11 12:15:45 tapan-laptop kernel: [   46.418460] [drm] TV-14: set mode NTSC 480i 0
May 11 12:18:51 tapan-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
May 11 12:18:51 tapan-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
May 11 12:18:51 tapan-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
May 11 12:18:51 tapan-laptop kernel: [    0.000000] Linux version 2.6.31-21-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 (Ubuntu 2.6.31-21.59-generic)
May 11 12:18:51 tapan-laptop kernel: [    0.000000] KERNEL supported cpus:
May 11 12:18:51 tapan-laptop kernel: [    0.000000]   Intel GenuineIntel
May 11 12:18:51 tapan-laptop kernel: [    0.000000]   AMD AuthenticAMD
May 11 12:18:51 tapan-laptop kernel: [    0.000000]   NSC Geode by NSC
May 11 12:18:51 tapan-laptop kernel: [    0.000000]   Cyrix CyrixInstead
May 11 12:18:51 tapan-laptop kernel: [    0.000000]   Centaur CentaurHauls
May 11 12:18:51 tapan-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
May 11 12:18:51 tapan-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
May 11 12:18:51 tapan-laptop kernel: [    0.000000]   UMC UMC UMC UMC
```

> **soltanis said:**
> Sounds like a hardware bug + a kernel panic. Does running other graphics/CPU intensive apps delay the problem? Perhaps if you run a GPU benchmark tool, does that help?

And yeah, we'll need as many kernel/system logs as can be scrounged.

Yes, playing WoW or warcraft delays the crash. In fact if i just keep WoW on all the time the laptop does not hang. However if i keep it minimized it will hang in sometime. Its like my laptop is possessed :P

---

