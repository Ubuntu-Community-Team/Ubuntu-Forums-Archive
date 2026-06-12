---
title: "Ubuntu not recognizing Overclock?"
date: 2012-08-31
forum: General Help
---

### Post by Philip11 on 2012-08-31
Hello, I am trying to overclock my Processor (AMD Athlon 64 X2 4200+) and there is a option in the BIOS for OC'ing but when I overclock and boot to Ubuntu Studio it acts as if nothing happened and cat /proc/cpuinfo gets me nowhere gives me the normal clock speed and I read disabling AMD Cool N Quiet fixes this but I don't see a option in the BIOS is it maybe listed under something else?


My Specs
Motherboard: NF61V-M2
CPU: AMD Athlon 64 4200+ X2
RAM 1 GB DDR2
OS: Ubuntu Studio 64 Bit

---

### Post by dcstar on 2012-09-01
> **Philip11 said:**
> Hello, I am trying to overclock my Processor (AMD Athlon 64 X2 4200+) and there is a option in the BIOS for OC'ing but when I overclock and boot to Ubuntu Studio it acts as if nothing happened and cat /proc/cpuinfo gets me nowhere gives me the normal clock speed and I read disabling AMD Cool N Quiet fixes this but I don't see a option in the BIOS is it maybe listed under something else?


My Specs
Motherboard: NF61V-M2
CPU: AMD Athlon 64 4200+ X2
RAM 1 GB DDR2
OS: Ubuntu Studio 64 Bit

Ubuntu reads and reports the numbers embedded in the CPU, it does not take into account anything else that is done.

---

### Post by Bachstelze on 2012-09-01
> **dcstar said:**
> Ubuntu reads and reports the numbers embedded in the CPU, it does not take into account anything else that is done.

Wrong. /proc/cpuinfo will report the clock rate at which the CPU is currently operating, and it can fluctuate over time.

@OP: It is most probably Cool n Quiet kicking it. Try doing something really CPU-intensive (so that CnQ will make the processor run at full speed), and cat /proc/cpuinfo again.

---

### Post by Philip11 on 2012-09-07
> **Bachstelze said:**
> Wrong. /proc/cpuinfo will report the clock rate at which the CPU is currently operating, and it can fluctuate over time.

@OP: It is most probably Cool n Quiet kicking it. Try doing something really CPU-intensive (so that CnQ will make the processor run at full speed), and cat /proc/cpuinfo again.
Tried that I opened Ubuntu Software Center, Blender, and GIMP and it barely ran then I checked and it was at the regular clock Speed 2200 MHz.

---

### Post by Cheesemill on 2012-09-07
Just opening lots of applications isn't CPU intensive, it just increases the RAM usage of your system. You need to run an application that actually fully maxes out the CPU for example cpuburn.
```
sudo apt-get install cpuburn
```
To run cpuburn just run one of the following commands depending on your processor:
```
burnP5 - is for Intel Pentium (with and without MMX processors);
burnP6 - is for Intel Pentium Pro, PentiumII, Pentium III, Celeron and later;
burnK6 - is for AMD K6;
burnK7 - is for AMD Athlon and Duron;
burnMMX - is for testing cache / memory interfaces on all CPU's with MMX;
burnBX - is an alternate cache / memory test for Intel CPU's. 
```
Then open another terminal and run
```
cat /proc/cpuinfo
```
again.

---

### Post by Philip11 on 2012-09-07
> **Cheesemill said:**
> Just opening lots of applications isn't CPU intensive, it just increases the RAM usage of your system. You need to run an application that actually fully maxes out the CPU for example cpuburn.
```
sudo apt-get install cpuburn
```To run cpuburn just run one of the following commands depending on your processor:
```
burnP5 - is for Intel Pentium (with and without MMX processors);
burnP6 - is for Intel Pentium Pro, PentiumII, Pentium III, Celeron and later;
burnK6 - is for AMD K6;
burnK7 - is for AMD Athlon and Duron;
burnMMX - is for testing cache / memory interfaces on all CPU's with MMX;
burnBX - is an alternate cache / memory test for Intel CPU's. 
```Then open another terminal and run
```
cat /proc/cpuinfo
```again.
I believe I have a K8 Processor but I could be wrong and I installed CPUBurn and ran burnk7 and burnk6 but it just sits there and does nothing I checked the CPU load and CPU 1 had 100% load CPU 2 had a normal load. and cat/proc/cpuinfo stayed at the normal 2200 MHz.

---

### Post by Philip11 on 2012-09-11
Anybody Else?

---

