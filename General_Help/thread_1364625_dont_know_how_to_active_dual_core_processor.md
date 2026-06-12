---
title: "dont know how to active dual core processor"
date: 2009-12-26
forum: General Help
---

### Post by coolubunt on 2009-12-26
hi guys..
i am newbie to ubuntu ...my system has intel Pentium core 2 duo processor..
i installed ubuntu 9.10 version yesterday..when i see the "system moniter" it shows my processor as single core CPU

and i used terminal command, it shows 
cat /proc/cpuinfo | grep '^processor' | wc -l
1

~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
stepping    : 6
cpu MHz        : 1596.000
cache size    : 3072 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips    : 5333.56
clflush size    : 64
power management:
what i do guys to get my dual core utilization..wasted around 10 hours :confused::confused::confused: to find the solution. if you have solution please tell me step by step method because i am newbie to ubuntu :(:( help pls...

---

### Post by dcstar on 2009-12-27
> **coolubunt said:**
> hi guys..
i am newbie to ubuntu ...my system has intel Pentium core 2 duo processor..
i installed ubuntu 9.10 version yesterday..when i see the "system moniter" it shows my processor as single core CPU
...........
what i do guys to get my dual core utilization..wasted around 10 hours :confused::confused::confused: to find the solution. if you have solution please tell me step by step method because i am newbie to ubuntu :(:( help pls...

This usually has nothing to do with Ubuntu, enable it in your BIOS.

---

