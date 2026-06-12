---
title: "Processor info incorrect"
date: 2011-03-12
forum: General Help
---

### Post by d4rkcell on 2011-03-12
Hi.

My system has an AMD 5000+ processor which has a frequency of 2.6GHz (2600MHz)

I am running ubuntu 64bit 10.10 The system info tool shows CPU speed as 1000 MHz. I also did cat /proc/cpuinfo and it shows the below.

```
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping    : 2
cpu MHz        : 1000.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
bogomips    : 2009.17
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping    : 2
cpu MHz        : 1000.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
bogomips    : 2009.17
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps
```

Does anyone have any idea why it is only reporting the CPU Frequency as 1000 MHz?

Now I am still somewhat of a noob when troubleshooting ubuntu and nux in general so please go easy on me.

I am going to check the processor settings in machine BIOS to make sure i am not being crazy. Any adivce or help would be neat.

Thanks

---

### Post by davidmohammed on 2011-03-12
I suspect that cpuinfo is simply reporting what the current processor speed is - your processor can scale back if its not doing very much.

To test this, right click the top panel and select "add to panel" - choose the cpu frequency scaling monitor

This should show the different scaling your processor is capable of.

Click on the monitor and choose "performance" - it should now default to the max speed of your processor.

---

### Post by d4rkcell on 2011-03-12
Very strange it would seem the values in the BIOS that I had set to AUTO were causing the processor to clock in at a lower than normal frequency. I changed the multiplier to 13 and set the FSB to 200 and it now shows as the correct speed. Not sure why on earth it defaulted to the wrong speed? Anyhow not a problem with ubuntu!

---

### Post by davidmohammed on 2011-03-12
try what I said above - I think what you have done is simply make the processor run at the maximum speed all the time.  Very little point in doing this - it will simply increase your electric bill...

---

### Post by d4rkcell on 2011-03-12
Hi thanks for the tip! I tried the CPU Frequency monitor and I think what you say is right. I changed the settings back to AUTO in the BIOS and now the monitor shows 38% or 1 GHz. I never knew this was a feature of ubuntu and thought it was something only laptops did. Thanks for the help :)

---

