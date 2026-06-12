---
title: "CPU: 32-bit or 64-bit?"
date: 2010-07-26
forum: General Help
---

### Post by hex444b on 2010-07-26
Although I have gone through a million threads with this same exact question, I am still a bit confused.

According to [http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/]("http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/"), my CPU is 64-bit because 'lm' is included in the flags when I type in 
```
cat /proc/cpuinfo
```
and get
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 95
model name	: AMD Athlon(tm) 64 Processor 3200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy
bogomips	: 2004.19
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

When I type in ```
lscpu
```, I get ```
Architecture:          i686
CPU op-mode(s):        64-bit
CPU(s):                1
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             AuthenticAMD
CPU family:            15
Model:                 95
Stepping:              2
CPU MHz:               1000.000
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K

``` and the CPU op-mode seems to be a dead giveaway that I have a 64-bit processor. However, my question is regarding the first line. Why does it say that I have a i686 (32-bit) architecture when the line below it says that I have a 64-bit processor? The only explanation that I can think of is that the architecture line is referring to the 32-bit kernel I have running. Can someone explain? 

When I type in ```
uname -m
``` I get ```
i686
``` but this is saying that I have a 32-bit kernel running and not necessarily a 32-bit CPU according to the site I mentioned above.

I read in another thread that all processors with "AMD" in the model name are 64-bit. Is this true?

Thanks for your help!

---

### Post by nmaster on 2010-07-26
you have an x86-64 (also called AMD64) architecture.  this means that you can run either a 64-bit or 32-bit OS.  you have chosen to run a 32-bit OS.

---

### Post by hex444b on 2010-07-26
> **neal.m.master said:**
> you have an x86-64 (also called AMD64) architecture.  this means that you can run either a 64-bit or 32-bit OS.  you have chosen to run a 32-bit OS.

Thanks for your response, but I am still a bit confused. Why is that the output of ```
lscpu
``` shows ```
Architecture: i686
``` instead of ```
Architecture: x86-64
``` according to your response?

---

### Post by sisco311 on 2010-07-26
Hi and welcome to the forums!

You pretty much answered your own question. You are running a 32-bit OS on top of a 64-bit processor.

---

### Post by sisco311 on 2010-07-26
> **hex444b said:**
> Thanks for your response, but I am still a bit confused. Why is that the output of ```
lscpu
``` shows ```
Architecture: i686
``` instead of ```
Architecture: x86-64
``` according to your response?

It's because *Architecture* refers to the architecture of the OS.

---

### Post by hex444b on 2010-07-26
Thank you!

---

