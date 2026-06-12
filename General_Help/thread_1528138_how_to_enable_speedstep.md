---
title: "how to enable speedstep"
date: 2010-07-10
forum: General Help
---

### Post by arjunak01 on 2010-07-10
how can i enable speed step on my pc. im using intel e5300 [http://ark.intel.com/Product.aspx?id=35300](http://ark.intel.com/Product.aspx?id=35300) and ubuntu 10.04. here is the output of cat /proc/cpuinfo
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Pentium(R)  CPU       E5300  @ 2.60GHz
stepping    : 10
cpu MHz        : 2600.369
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni monitor tm2 ssse3 lahf_lm
bogomips    : 5200.73
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Pentium(R)  CPU       E5300  @ 2.60GHz
stepping    : 10
cpu MHz        : 2600.369
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni monitor tm2 ssse3 lahf_lm
bogomips    : 5199.91
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```when i try to run sudo /etc/init.d/cpufreqd, i get
```
 * Starting CPU Frequency daemon cpufreqd                                [fail] 

```and when running modprobe  p4-clockmod```
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.32-24-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): No such device
```There is no cpufreq folder inside /sys/devices/system/cpu/cpuX and the /sys/devices/system/cpu/cpufreq folder is empty. what should i do.

---

### Post by WorMzy on 2010-07-10
Have you enabled speedstep in the bios?

Chances are that cpufreqd is already running, which is why your start command fails.

I've never tried p4-clockmod myself, is it an alternative to acpi_cpufreq? I have an Intel E8500 and acpi_cpufreq works fine.

---

### Post by arjunak01 on 2010-07-10
frequency scaling monitor applet says that frequency scaling is unsupported. do you think i need to recompile the kernal

---

### Post by WorMzy on 2010-07-10
No, that's a sign that you haven't enabled speedstep in the bios. If you have enabled it, and you're getting that message, then there's nothing you can do.

Do you know how to access the bios? You need to press a specific key immediately after the computer POSTs, immediately after you first power on your PC. As for what the key is, it varies from motherboard to mother board, but try Esc and/or Del, those are quite common choices.

---

### Post by arjunak01 on 2010-07-10
EIST is enabled in the bios. and my motherboard is DG31PR [http://www.intel.com/Products/Desktop/Motherboards/DG31PR/DG31PR-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/DG31PR/DG31PR-overview.htm). I tried it in windows by changing power options to max battery and then opened system  properties but it doesnt make any change. the clock speed is still reported as 2.6GHz. but the vcore voltage drops from 1.27 to 1.10 when the cpu is inactive.

---

### Post by WorMzy on 2010-07-10
In the bios, is your CPU multiplier set to "auto" (or equivalent)? It has to be set to auto to work (but I'd expect the speedstep option to be disabled and hidden if it wasn't, so chances are it already is). If it's not working on Windows either, then there's either something still wrong in the BIOS, or you can't use it for some unknown reason.

---

### Post by arjunak01 on 2010-07-10
in the bios cpu and motherboard temperatures are stuck at 84 and 32C. there must be something wrong with the bios

---

### Post by WorMzy on 2010-07-10
Either that or your CPU is about to explode. :P

You may want to consider flashing the bios to see if that helps; that link you posted lists quite a few bios updates for that motherboards, the latest being from four months ago, so chances are this is a known issue and has been fixed.

Still, flashing your bios is a risky procedure, and you risk bricking your motherboard if something goes wrong (e.g. powercut during the update procedure), so it's up to you to decide what course of action you want to take.

---

