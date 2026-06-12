---
title: "Kernel Choice"
date: 2006-02-21
forum: General Help
---

### Post by bobpaul on 2006-02-21
I'm running an AMD Barton (AthlonXP 32bit) system. As I understand it, the origional AMD Athlon was the K7, then there was the K75, and then the Thunderbird followed by the Athlon XP processors. But then I also thought the K8 was the AMD64 architecture, which means I must be running a K7.

So I'm confused. Do I want the i686 kernel or the K7 kernel? Both seem to run, but I'm sure one is more specific to my hardware and will thus work a little better/faster/whatever.

---

### Post by heimo on 2006-02-21
linux-686
> Description: Complete Linux kernel on PPro/Celeron/PII/PIII/PIV.
 This package will always depend on the latest complete Linux kernel available
 for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV. 
 linux-k7
> 

Description: Complete Linux kernel on AMD K7.
This package will always depend on the latest complete Linux kernel available
 for AMD Duron/Athlon.


Both will work and there will be no perceivable performance difference.

---

### Post by az on 2006-02-21
I think the k7 would be better.  There are a few multimedia functions that a pentium does not have.  Also, the difference between a 386 kernel and either a 686 for pentium or k7 for AMD is pronounced for lower-end CPUs (like 300 MHz to 900Mhz).  The diference is less pronounced for older or newer hardware.  Your mileage may vary...

---

