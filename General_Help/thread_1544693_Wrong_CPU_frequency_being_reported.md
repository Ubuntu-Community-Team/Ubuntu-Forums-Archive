---
title: "Wrong CPU frequency being reported?"
date: 2010-08-02
forum: General Help
---

### Post by GCT on 2010-08-02
So I've got a dual core  Core 2 6600 in my system, specced at 2.4GHz, but for some reason every indicator I can find says I'm running between 600MHz and 900MHz.  I'm on 10.04 and the frequencing scaling applet says 900MHz when I have it on performance, and it'll drop to 600MHz when it's in ondemand mode.

The output of my /proc/cpuinfo:

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 4798.96
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 600.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 4800.07
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

Any idea how this happened or how I can fix it?  I haven't been screwing with my frequency scaling settings or anything... Just reinstalled as a matter of fact.

---

### Post by AlphaLexman on 2010-08-02
Are you looking at the processor speed under a heavy load, or under low demand?
Many modern processors 'scale down' the MHz to save on power consumption.

---

### Post by GCT on 2010-08-02
This is under regular load, but the frequency setting is set to "performance" and I've never seen it down at 600MHz before...  I just compiled boost a little bit ago and it never went above 900 either.

---

