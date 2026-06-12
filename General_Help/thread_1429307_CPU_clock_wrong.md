---
title: "CPU clock wrong"
date: 2010-03-13
forum: General Help
---

### Post by disk11 on 2010-03-13
System:
Asrock X58 Extreme
Intel i7 920 w/ stock cooler, HT on
6GB Gskill Pi pc16000
Geforce2 MX
200GB Maxtor SATA
Lite-On DVD-RW SATA
OCZ 600W ModX

OS: Ubunt 9.10 x64

I have the CPU set to 12x multi and 150 bclock in the BIOS, which should be 1800 mhz.  However Ubuntu seems to think I still have the 20x multi on.

Here is the output of /proc/cpuinfo for one of the cores (no need to see it 7 more times):
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
stepping	: 5
cpu MHz		: 3002.314
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology tsc_reliable nonstop_tsc pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6004.62
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

I'm pretty sure I have all the power saveing BIOS features off (C1E, etc.).  Is this a Ubuntu issue or do I have a BIOS setting messing with me?

---

### Post by dcstar on 2010-03-13
> **disk11 said:**
> 
I have the CPU set to 12x multi and 150 bclock in the BIOS, which should be 1800 mhz.  However Ubuntu seems to think I still have the 20x multi on.
.........

AFAIK Ubuntu only reads and reports the "official" settings from the CPU, not the stuff that changes in the BIOS.

Run benchmarks to see if the changes are real.

---

### Post by disk11 on 2010-03-14
Almost no change according to freebench between 12x and 16x.

---

