---
title: "Laptop overheating in Ubuntu (Can you help?)"
date: 2010-06-01
forum: General Help
---

### Post by thrainpa on 2010-06-01
My laptop is an Acer Travelmate 7530G, it runs an AMC Athlon X2 64 2.1Ghz CPU, 2GB RAM and an ATI Radeon HD3470 Hybrid X2 512MB.

In Ubuntu (all versions) the temperature sensor goes up to around 99C and apparently sometimes reaches up to 109C !
The laptop itself gets very hot (as one would imagine), and the fan is on highest constantly.

But in windows this problem is not present.

Can anyone help identify/solve this problem?

---

### Post by lrgmmc on 2010-06-01
have you tried cpu scaling.

---

### Post by thrainpa on 2010-06-01
Yes, on Powersave lm-sensors says 93C.

---

### Post by lrgmmc on 2010-06-01
can you post ```
cat /proc/cpuinfo
```

---

### Post by thrainpa on 2010-06-01
thrainpa@NIGHT:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Athlon(tm) X2 Dual-Core QL-64
stepping	: 1
cpu MHz		: 1050.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4199.45
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Athlon(tm) X2 Dual-Core QL-64
stepping	: 1
cpu MHz		: 1050.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4200.22
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

---

### Post by philinux on 2010-06-01
see the General Help forum sticky. Thinks it's next to last post.

---

### Post by thrainpa on 2010-06-01
philinux - That fix says it is specific for Intel Machines. I am running on an AMD Athlon X2 64 running Ubuntu 64-bit.

---

### Post by philinux on 2010-06-02
> **thrainpa said:**
> philinux - That fix says it is specific for Intel Machines. I am running on an AMD Athlon X2 64 running Ubuntu 64-bit.

Ah, missed that, well you get a free bump then instead!

---

