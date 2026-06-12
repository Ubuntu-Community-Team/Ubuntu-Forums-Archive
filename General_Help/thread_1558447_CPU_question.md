---
title: "CPU question"
date: 2010-08-22
forum: General Help
---

### Post by conradin on 2010-08-22
Hi all,
I have a Penguin Niveus 805.
```

bash-3.1# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :                   Intel(R) Xeon(TM) CPU 3.60GHz
stepping        : 3
cpu MHz         : 3600.214
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl est tm2 cid cx16 xtpr
bogomips        : 7202.88
clflush size    : 64
cache_alignment : 128
**address sizes   : 36 bits physical, 48 bits virtual**
power management:

```

what virtual address?
also, I have 2 cpus on board, but cpuinfo shows 4. Is that because its 64 bit running as 2 32-bit, or because both processors are dual core?

---

### Post by deddokatana on 2010-08-22
and why does it say only one core?

---

### Post by anirudhtomer on 2010-08-22
First of all u have a single CPU core otherwise u would have got an entry 
cpu cores : 2
& as soon as u would have done "cat /proc/cpuinfo" u would have got tables for both but I think u got only one & that's what u posted here.

& follow this link [http://www.linuxquestions.org/questions/linux-hardware-18/address-sizes-in-cpuinfo-757456/](http://www.linuxquestions.org/questions/linux-hardware-18/address-sizes-in-cpuinfo-757456/)
for understanding the virtual & physical address funda.

---

### Post by cool Cpu on 2010-08-22
cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Quad  CPU   Q9000  @ 2.00GHz
stepping    : 10
cpu MHz        : 1600.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority
bogomips    : 3990.68
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Quad  CPU   Q9000  @ 2.00GHz
stepping    : 10
cpu MHz        : 1600.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority
bogomips    : 3989.98
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by anirudhtomer on 2010-08-22
now even I am confused to see this...this guy has got 4 cores...so entries should be there for each core...I mean if u have a "core id" with just two values 0 & 1 that means u have two cores one with ID 0 & other with ID 1...but the above post shows 4 cores & just two ID's.

---

### Post by cascade9 on 2010-08-22
> **conradin said:**
> also, I have 2 cpus on board, but cpuinfo shows 4. Is that because its 64 bit running as 2 32-bit, or because both processors are dual core?

2048kB cache xeons ("irwindale") have hyperthreading. 

Its not a 'real' core but appears in things like cpuinfo as a core, but it is still a sinlge core CPU.

---

