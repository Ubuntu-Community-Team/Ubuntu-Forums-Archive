---
title: "Incorrect CPU speed in /proc/cpuinfo with AMD Athlon II X4 630"
date: 2010-09-04
forum: General Help
---

### Post by benjorino on 2010-09-04
Hi,

I have an AMD Athlon(tm) II X4 630 Processor, which should be 2.6GHz quad core, yet  
  
cat proc/cpuinfo

displays it as 4 x 800MHz.
  
Anybody got any idea why this may be?

Also, is it a problem?

Does this mean Ubuntu is not using all my available processing power?

I am using Ubuntu 10.04 64-bit.


Thanks,
Ben

---

### Post by benjorino on 2010-09-04
Full output of cat /proc/cpuinfo:

```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 5
model name	: AMD Athlon(tm) II X4 630 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5615.08
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

It prints four of these, one for each processor. I've only posted one to save space.

---

### Post by MooPi on 2010-09-04
Your computer has throttling capabilities. When your computer is doing simple tasks that only require limited CPU cycles it is throttled down. But when you do something CPU intensive your processor will ramp up. If you encode a music CD check the cpu speed then. I have nothing but AMD  and this is how it works. If you are comfortable with entering your bios, you can turn off something called Cool & Quiet in Asus motherboards. With other vendors they call it by similar names, you'll just have to look. This is my CPU which is actually capable of 2.7 GHz

```
processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 6
model name	: AMD Athlon(tm) II X2 240 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5625.55
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
```

---

### Post by benjorino on 2010-09-05
Ahh awesome - thank you!

I ran some cpu intensive code and checked again:

```

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 5
model name	: AMD Athlon(tm) II X4 630 Processor
stepping	: 2
cpu MHz		: 2800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5615.98
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```

:)
Thanks for the reply.

---

