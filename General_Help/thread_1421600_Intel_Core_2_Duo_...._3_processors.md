---
title: "Intel Core 2 Duo .... 3 processors??"
date: 2010-03-04
forum: General Help
---

### Post by caradeporra on 2010-03-04
So I have an Intel Core 2 Duo t7250 processor.  I have screenlets installed and am using the meter screenlet.  It has the option of cpu0, cpu1, and cpu2.  I just assumed since it was dual core cpu2 wouldnt work and never tried it....until today, dun dun dun(sorry for the gayness - it sounded way cooler in my head).  Anyway, to my surprise the meter actually works, and at first i assumed it would just mock one of the other meters but it doesn't it seems to actually be monitoring something else.  Can anyone explain this to me?

---

### Post by Cabs21 on 2010-03-04
that is both of your processor speed combined.

---

### Post by mcduck on 2010-03-04
One of the values is actually a combined value for all processors.

edit: I remembered that Core 2 would have hyperthreading , which it actually doesn't have, so the other option I had here was pretty much nonsense. Anyway, you can run "*cat /proc/cpuinfo*" in a terminal to get a detailed info about your CPU, and how many CPUs/cores you have

---

### Post by wojox on 2010-03-04
I think it's mcduck's hyperthreading theory. Post back.

---

### Post by caradeporra on 2010-03-04
Sweet!  thanks guys for the info - that really clears up my clouded thoughts about hidden secret passageways to new and unexplained processors.  I thought i found the next best thing to hidden soundtracks on cd's!

---

### Post by wojox on 2010-03-04
I didn't know screenlets were that smart.

---

### Post by mcduck on 2010-03-04
> **caradeporra said:**
> Sweet!  thanks guys for the info - that really clears up my clouded thoughts about hidden secret passageways to new and unexplained processors.  I thought i found the next best thing to hidden soundtracks on cd's!

Just as a curiosity, there actually *is* such thing as hidden processor cores... ;)

Some of the cheap 3-core AMD CPUs are actually same models as the 4-core models, with one core deactivated. In some cases the deactivated core isn't actually broken and can be enabled again to get one extra core for free...

---

### Post by cascade9 on 2010-03-04
> **mcduck said:**
> Some of the cheap 3-core AMD CPUs are actually same models as the 4-core models, with one core deactivated. In some cases the deactivated core isn't actually broken and can be enabled again to get one extra core for free...

Not just the triple-core models, there are also dual-cores that can be 'unlocked' to give you 4 cores. 

You have to have a motherobard with ACC (advanced clock calibration) to do this though.

---

### Post by mcduck on 2010-03-04
> **cascade9 said:**
> Not just the triple-core models, there are also dual-cores that can be 'unlocked' to give you 4 cores. 

You have to have a motherobard with ACC (advanced clock calibration) to do this though.

true, or some nice skills with modifying your hardware.. Some new motherboards even have a button to enable the extra coresfor you. :) I was actually coming back to add a "for example" to the 3-core AMD CPU thing.

Anyway most of the cheaper CPU's are actually same as higher price models, only with some features or parts of the processor disabled and set to run at lower speed. It's cheaper to manufacture one model and sell the lower-quality stuff or units that have some manufacturing errors as cheap models instead of specifically manufacturing two separate models and throwing all not-perfect nits away. And sometimes there isn't really anything wrong with the units sold as cheaper models...

---

### Post by caradeporra on 2010-03-04
> **mcduck said:**
> true, or some nice skills with modifying your hardware.. Some new motherboards even have a button to enable the extra coresfor you. :) I was actually coming back to add a "for example" to the 3-core AMD CPU thing.

Anyway most of the cheaper CPU's are actually same as higher price models, only with some features or parts of the processor disabled and set to run at lower speed. It's cheaper to manufacture one model and sell the lower-quality stuff or units that have some manufacturing errors as cheap models instead of specifically manufacturing two separate models and throwing all not-perfect nits away. And sometimes there isn't really anything wrong with the units sold as cheaper models...

VERY interesting guys.  I had heard of this before as far as the cache goes, i didnt know that worked for processors too.  Any ideas if my processor can be over clocked to use other processors or cache?

---

### Post by linux00 on 2011-03-26
I have a Core 2 Duo T5550, screenlets showing cores 0, 1 and 2, but none of the graphs are averages of the other two or the other two added up. Sometimes 0 has more used, sometimes 1, but very rarely 2, and "cat /proc/cpuinfo" says "cpu cores = 2".

---

### Post by antaios256 on 2011-03-26
im actually quite interested in the unlocking of cores and a bit curious. im running an i7 q720

and when i run the "cat /proc/cpuinfo" i actually show up with 8 cores....  any ideas on this. i mean i know i have hyper threading but should it really be showing as 8 separate cores?

```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
stepping    : 5
cpu MHz        : 933.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 3192.03
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
stepping    : 5
cpu MHz        : 933.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 3191.99
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
stepping    : 5
cpu MHz        : 933.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 3191.90
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
stepping    : 5
cpu MHz        : 933.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 3192.01
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 4
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
stepping    : 5
cpu MHz        : 933.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 3192.08
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 5
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
stepping    : 5
cpu MHz        : 933.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 3192.16
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 6
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
stepping    : 5
cpu MHz        : 933.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 5
initial apicid    : 5
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 3192.30
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 7
vendor_id    : GenuineIntel
cpu family    : 6
model        : 30
model name    : Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
stepping    : 5
cpu MHz        : 933.000
cache size    : 6144 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 7
initial apicid    : 7
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 3192.02
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

---

