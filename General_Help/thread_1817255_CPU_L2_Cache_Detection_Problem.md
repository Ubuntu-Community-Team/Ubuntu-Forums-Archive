---
title: "CPU L2 Cache Detection Problem"
date: 2011-08-03
forum: General Help
---

### Post by UCSBGauchosRock on 2011-08-03
I have kind of a large problem on my 64 bit ubuntu machine. I have 3gb ram and a pentium d 820 processor(with 2MB L2 cache as shown by BIOS) but running "cat /proc/cpuinfo" outputs the following: 

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) D CPU 2.80GHz
stepping    : 4
cpu MHz        : 2800.669
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl cid cx16 xtpr
bogomips    : 5601.33
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

And that says that only 1MB of the L2 cache is being detected. I would like to utilize the cache to it's full potential so could anybody tell me what is wrong? :(

EDIT: Oh I just realized my problem and saw that this was actually a dual core processor. I think I only copy and pasted info from only one of the cores. Sorry about that. I have requested deletion of this post

---

