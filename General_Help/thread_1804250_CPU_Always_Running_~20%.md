---
title: "CPU Always Running ~20%"
date: 2011-07-14
forum: General Help
---

### Post by steevven1 on 2011-07-14
On Ubuntu 11.04, "top" reveals that my CPU is always running about 20% in the "si" state, even when nothing is running at all. I don't know what this means, but it is making my computer hot and draining my battery like CRAZY.

Any ideas?

---

### Post by idoitprone on 2011-07-14
> **steevven1 said:**
> On Ubuntu 11.04, "top" reveals that my CPU is always running about 20% in the "si" state, even when nothing is running at all. I don't know what this means, but it is making my computer hot and draining my battery like CRAZY.

Any ideas?

post the output of 

```
cat /proc/cpuinfo
```
Do you have a gpu?
From the looks of it, it is probably the fact that you are using a more resource hungry destkop. You might want to change desktop such as installing xubuntu or lubuntu

---

### Post by psusi on 2011-07-14
si means servicing interrupts.  It sounds like you have some broken hardware that won't stop interrupting the cpu.  cat /proc/interrupts and see if you can identify which one is going bonkers.

---

### Post by steevven1 on 2011-07-15
Interestingly, this all started when I installed "xubuntu-desktop" and started using xfce.

It actually doesn't happen all the time, but it gets triggered by something which I can't identify, and never goes away until I reboot, and eventually starts up again.


CPU Info:

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5383.02
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5382.53
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5382.57
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5382.57
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by wildmanne39 on 2011-07-15
Hi, you might try running top from a terminal it will show you what is using the cpu.

---

### Post by idoitprone on 2011-07-15
> **steevven1 said:**
> Interestingly, this all started when I installed "xubuntu-desktop" and started using xfce.


model name    : Intel(R) Core(TM) i7-2620M CPU @ 2.70GHz

ok this is problably not a cpu problem, but a software problem. Unfornately, i am a complete idoit. wildmanne39 is wiser.

---

### Post by wildmanne39 on 2011-07-15
Hi, also I am sorry I see that you have already used top. You might want to look at your dmesg log and see if you see any errors.

---

