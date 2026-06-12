---
title: "question about /proc/cpuinfo"
date: 2010-01-02
forum: General Help
---

### Post by Iksf on 2010-01-02
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping    : 13
cpu MHz        : 1000.000
cache size    : 2048 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3657.71
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping    : 13
cpu MHz        : 1000.000
cache size    : 2048 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips    : 3657.42
clflush size    : 64
power management:

```

Is 1000Mhz the correct value for a 1.83ghz processor, it doesnt look right but i could be completly wrong, anyone know if this is in order and if not what i should do

---

### Post by dcstar on 2010-01-02
> **Iksf said:**
> 
........
Is 1000Mhz the correct value for a 1.83ghz processor, it doesnt look right but i could be completly wrong, anyone know if this is in order and if not what i should do

When you are not using CPU resources the system automatically throttles it down to save power.

---

### Post by x33a on 2010-01-02
If it is a laptop then maybe it is working in underclocked mode for power saving.

---

### Post by Iksf on 2010-01-03
Ok, that does seem to be the core of the issue, thanks. But even when playing a heavy game (it is indeed a laptop btw) it sometimes is below 1833mhz, would this cause a decrease in performance or is it only done when the CPU is underused?

---

### Post by audiomick on 2010-01-03
> **Iksf said:**
> Ok, that does seem to be the core of the issue, thanks. But even when playing a heavy game (it is indeed a laptop btw) it sometimes is below 1833mhz, would this cause a decrease in performance or is it only done when the CPU is underused?

I would think that if you are not noticing any problems with your game or anything, that it is probably in order. As I understand it, games are harder on the video card than the actual CPU.

It might be worth trying to research the "stepping" value. I think that has to do with the (regulation of the) cpu speed. Does this value change with different values for "cpu MHz" ?

---

### Post by Iksf on 2010-01-03
Ok cheers, great response time too :D

---

