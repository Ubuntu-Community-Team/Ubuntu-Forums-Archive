---
title: "how to know which bit is my processor"
date: 2011-12-04
forum: General Help
---

### Post by shubham1 on 2011-12-04
tell my processor is 32bit or 64bit
info of processor throught system info is 
AMD Athlon(tm) II X4 635 Processor × 4 
nether 11.10 amd64 bit worked
nether 12.04 amd64 bit worked

---

### Post by mikewhatever on 2011-12-04
It's a 64bit CPU, which means you can use both 32bit and 64bit software. Generally, most of the recent ADM/Intel CPUs are 64bit, but if you want to make sure, google.

[http://www.cpu-world.com/CPUs/K10/AMD-Athlon%20II%20X4%20635%20-%20ADX635WFK42GI%20%28ADX635WFGIBOX%29.html](http://www.cpu-world.com/CPUs/K10/AMD-Athlon%20II%20X4%20635%20-%20ADX635WFK42GI%20%28ADX635WFGIBOX%29.html)

---

### Post by shubham1 on 2011-12-04
> **mikewhatever said:**
> It's a 64bit CPU, which means you can use both 32bit and 64bit software. Generally, most of the recent ADM/Intel CPUs are 64bit, but if you want to make sure, google.

[http://www.cpu-world.com/CPUs/K10/AMD-Athlon%20II%20X4%20635%20-%20ADX635WFK42GI%20%28ADX635WFGIBOX%29.html]("http://www.cpu-world.com/CPUs/K10/AMD-Athlon%20II%20X4%20635%20-%20ADX635WFK42GI%20%28ADX635WFGIBOX%29.html")
i think my machine is 32 bit as no 64 bit amd op is running secondly one man said to me that you system is 32bit thats your problem

---

### Post by plucky on 2011-12-04
> **shubham1 said:**
> i think my machine is 32 bit as no 64 bit amd op is running secondly one man said to me that you system is 32bit thats your problem

What operating system are you running?

From a terminal ```
cat /proc/cpuinfo
uname -a
``` and post the results.

---

### Post by shubham1 on 2011-12-04
32 bit intel iso image

---

### Post by shubham1 on 2011-12-04
```
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 5
model name    : AMD Athlon(tm) II X4 635 Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
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
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips    : 5826.60
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 5
model name    : AMD Athlon(tm) II X4 635 Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
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
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips    : 5826.54
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 5
model name    : AMD Athlon(tm) II X4 635 Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips    : 5826.46
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 5
model name    : AMD Athlon(tm) II X4 635 Processor
stepping    : 3
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips    : 5826.51
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
```

---

### Post by digithal on 2011-12-04
Your **[CPU]("http://goo.gl/Zslvq")** is 64-Bit compatible. You could run both i386 and amd64 images.
> **shubham1 said:**
> 32 bit intel iso image
This:
[quote=Jon Lasser]The 64-bit version is typically called 'amd64'  because AMD developed the 64-bit instruction extensions. (AMD extended  the x86 architecture to 64 bits while Intel was working on Itanium, but  Intel later adopted those same instructions.)  The 32-bit version is called i386, because Intel originated the 32-bit instruction set used on these chips.
  You can run the 64-bit version on virtually any 64-bit capable x86  compatible chip, and the 32-bit version on any modern x86-compatible  chip.
  Depending on how you write your software, it may or may not need to  be rewritten for 64 bits. (Generally, compiled software will need  changes, but not all interpreted software -- e.g., Python or Perl --  will require changes.)[/quote]
[RIGHT][Source]("http://superuser.com/questions/128496/why-is-64-bits-version-called-amd64-and-32-bits-version-called-i386")[/RIGHT]

---

### Post by shubham1 on 2011-12-05
> **digithal said:**
> Your **[CPU]("http://goo.gl/Zslvq")** is 64-Bit compatible. You could run both i386 and amd64 images.

This:

[RIGHT][Source]("http://superuser.com/questions/128496/why-is-64-bits-version-called-amd64-and-32-bits-version-called-i386")[/RIGHT]
thanks

---

### Post by digithal on 2011-12-05
> **shubham1 said:**
> thanks
You are welcome! :)

---

