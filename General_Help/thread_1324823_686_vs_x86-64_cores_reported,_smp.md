---
title: "686 vs x86-64: cores reported, smp"
date: 2009-11-12
forum: General Help
---

### Post by sloggerkhan on 2009-11-12
So I've noticed that on my dual core desktop running 64 bit ubuntu I only have 1 CPU reported in system monitor, while the 686/386 version of ubuntu reports 2 and shows their use level separately. 

Why is this? Does 64 bit ubuntu not use smp or fully use both cores?

```

$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) X2 Dual Core Processor BE-2350
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2008.92
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

```

As can be seen, it only reports 1 core...

---

