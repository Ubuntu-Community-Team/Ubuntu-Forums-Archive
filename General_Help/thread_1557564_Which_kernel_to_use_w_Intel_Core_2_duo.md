---
title: "Which kernel to use w/ Intel Core 2 duo"
date: 2010-08-20
forum: General Help
---

### Post by MechWarrior001 on 2010-08-20
I've read that you can use specialized kernels for your hardware, and I was wondering if there's a kernel I can use for my Intel Core 2 duo. I read in a previous post about using a "smp" variant, but kinda wanted some confirmation. Here's CPU info:

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping    : 13
cpu MHz        : 1200.000
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
bogomips    : 4399.25
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping    : 13
cpu MHz        : 1200.000
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
bogomips    : 4399.87
clflush size    : 64
power management:

```

Also, are customized kernels required for 64bit?

---

### Post by Ginsu543 on 2010-08-22
My previous rig was based on the C2D E6600 and it handled every normal kernel release from 9.04 --> 9.10 --> 10.04 just fine. I wouldn't worry too much about special kernels because C2D doesn't need them. Currently, my C2D is powering my HTPC running the latest 2.6.32-24 kernel for Ubuntu 10.04.

---

