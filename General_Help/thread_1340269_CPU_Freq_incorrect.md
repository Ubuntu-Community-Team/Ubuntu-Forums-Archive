---
title: "CPU Freq incorrect?"
date: 2009-11-28
forum: General Help
---

### Post by fowie on 2009-11-28
Ubuntu 9.10 on an Abit IL-90MV with 2GB ram and a Pentium Core 2 Duo 2.1Ghz.  In ubuntu, cat /proc/cpuinfo shows my cpus as:
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz
stepping	: 6
cpu MHz		: 1300.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 4333.26
clflush size	: 64
power management:

```
but I can't get the CPU frequency up to 2.1?  What's going on?

---

### Post by SlugSlug on 2009-11-28
most likley Intel speedstep, it only kicks in to 2.1 as and when it needs to - power saving thing quite a nice touch, mine is 2.3 most of the time its 2, 

[http://en.wikipedia.org/wiki/SpeedStep](http://en.wikipedia.org/wiki/SpeedStep)

---

### Post by fowie on 2009-11-28
That's what I would think, but right now I'm doing a handbrake DVD encode using x.264 and it has "maxed" both CPUs to 1.3.  Not to mention if I change the settings in the CPU Freq applet on the taskbar, it only goes from 600Mhz to 1.3Ghz, and setting it to performance just locks it at 1.3Ghz.  I even tried forcing it using 
```

sudo cpufreq-set -c 1 -f 2.16GHz

```
but it didn't change the speed.  Any other ideas?

---

### Post by fowie on 2009-11-28
Output of cpufreq-info:
```

analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 1.30 GHz
  available frequency steps: 1.30 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 600 MHz and 1.30 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.30 GHz.
  cpufreq stats: 1.30 GHz:0.00%, 1000 MHz:0.00%, 800 MHz:0.00%, 600 MHz:0.00%  (1966)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 600 MHz - 1.30 GHz
  available frequency steps: 1.30 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 600 MHz and 1.30 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.30 GHz.
  cpufreq stats: 1.30 GHz:0.00%, 1000 MHz:0.00%, 800 MHz:0.00%, 600 MHz:0.00%  (21948)

```

---

### Post by shaggy999 on 2009-11-28
If your system shows 600 Mhz -> 1.3 Ghz and it's says it's running at 1.3 Ghz then your system is actually running at 2.1 GHz. The problem is that the "scaling" utility is improperly determining what 100% of your CPU speed is. It's "cosmetic" in nature. I ran into this same problem with my old laptop. There is a fix for this, but I can't remember what it was.

In short, your system is running at full speed, but when it says 1.3 GHz it actually means 2.1 GHz.

---

### Post by mxc1090 on 2010-02-25
Sorry to dig up a semi-old thread, but does anyone know what fix shaggy ^^^ is referring to?  I believe I have this same problem.

---

