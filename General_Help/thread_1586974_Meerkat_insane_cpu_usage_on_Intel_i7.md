---
title: "Meerkat insane cpu usage on Intel i7"
date: 2010-10-02
forum: General Help
---

### Post by jrevillini on 2010-10-02
Anyone having insane CPU usage after upgrading from Lucid to Meerkat, espcially if running a multicore processor?  I have the Intel i7 (quad-core) and as you can see in the attchment, all cores are working pretty damn hard, yet I have nothing running, and if I look at CPU usage in the processes list, no processes report using any CPU.

The CPU usage mostly affects mouse movement and typing, occasionally pausing and then catching up, and it also affects watching video greatly.  In Lucid, everything was really smooth and finely tuned.

This is a 64-bit version of ubuntu, if that makes any difference.  Can anyone help me troubleshoot the issue or shall I file a bug?  I might need help with filing since I don't know what would be helpful to the developers to know.

Thanks,
Jim

---

### Post by davrosuk on 2010-10-02
I think I saw something similar myself on some Westmere kit. I loaded the live CD on a DL380G7 and noticed a few cores working hard with no associated processes. I didn't look into it as I was only running a few random tests before putting ESX on it. Probably worth running top or htop as root to find out what process is grabbing the CPU.

If nothing interesting presents looking at that... I'm sure other folks on here will have other (better) suggestions but one thing I always like to eliminate in these situations is the kernel. If you grab the latest mainline kernel from the ppa you can quickly and safely compare the shipped version against 2.6.36-rc6. At least that's a starting point!

---

### Post by envygeeks on 2010-10-02
My personal computer (which is an i7) has not experienced this problem. Perhaps you need to actually see what is using the CPU time.  The processes tab can be set to show all processes (root or not) and can also be set to organize by CPU used.  That is your first step to try and diagnose...

---

### Post by jrevillini on 2010-10-02
htop shows high CPU usage while no processes are using much processor at all.  It's so nuts.  I'll try getting the latest and greatest kernel via ppa as you suggested.

---

### Post by jrevillini on 2010-10-02
> **envygeeks said:**
> My personal computer (which is an i7) has not experienced this problem. Perhaps you need to actually see what is using the CPU time.  The processes tab can be set to show all processes (root or not) and can also be set to organize by CPU used.  That is your first step to try and diagnose...

Did you upgrade or install fresh?

---

### Post by jrevillini on 2010-10-02
Upgrading the kernel seems to have helped.  everything is running a lot more smoothly.  no mouse hiccups nor typing hangs, and the processors seem pretty happy.

ALT+printscreen isn't working, but that's probably something utterly different.

Thanks!

---

### Post by davrosuk on 2010-10-03
No worries.

Out of interest, which i7 do you have?

---

### Post by jrevillini on 2010-10-03
Intel Core i7-920 Bloomfield 2.66GHz 4 x 256KB L2 Cache 8MB L3 Cache LGA 1366 130W Quad-Core Processor

---

### Post by pav5088 on 2010-10-05
I've had exactly the same issue on a Presario CQ62 /w pentium dual core ie. high CPU usage associated with keyboard and/or touchpad lockups.  Upgrading the kernel seems to have solved this for me.  I've given the output of /proc/cpuinfo.  If any more information is required let me know.

cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
stepping    : 10
cpu MHz        : 1200.000
cache size    : 1024 KB
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
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dts
bogomips    : 4588.70
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
stepping    : 10
cpu MHz        : 1200.000
cache size    : 1024 KB
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
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm dts
bogomips    : 4588.45
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by jrevillini on 2010-10-05
Some of the device drivers which work on the older kernel stop working when I load the latest.  Does that mean device drivers are kernel-specific?  Just trying to learn.

In this case, I'm talking about the sound driver.

---

