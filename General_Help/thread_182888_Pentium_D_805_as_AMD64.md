---
title: "Pentium D 805 as AMD64?"
date: 2006-05-27
forum: General Help
---

### Post by msekolpsu on 2006-05-27
I'm running a new install of Ubuntu on my new Pentium D 805 machine and for some reason, it's reporting it as an AMD64.  This means that I can't run the linux-686-smp (because the ones I see are all for i386).

Any thoughts?  From cat /proc/cpuinfo, I get

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :              Intel(R) Pentium(R) D  CPU 2.66GHz
stepping        : 7
cpu MHz         : 3806.453
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips        : 7520.25
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

but when I try to run linux-686-smp, it states  package architecture (i386) does not match system (amd64)

Total Linux noob btw!  Thanks!

---

