---
title: "CPU frequency is Unknown!?"
date: 2011-02-07
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-02-07
I wanted to be able to see the frequency my cpu is running at 
[QUOTE="xfce4-cpufreq-plugin"]CPUFreq support is not present.
The CPUFreq Monitor will not function this session.[/QUOTE]
```
~$ cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
~$ hwinfo --cpu
01: None 00.0: 10103 CPU                                        
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 15.2.9 "Intel(R) Pentium(R) 4 CPU 2.80GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,up,pebs,bts,cid,xtpr
  Clock: 2793 MHz
  BogoMips: 5586.94
  Cache: 512 kb
  Units/Processor: 1
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by lukeiamyourfather on 2011-02-07
Does that processor even have speed stepping? I don't think it does, where it says idle states.

[http://ark.intel.com/Product.aspx?id=27447](http://ark.intel.com/Product.aspx?id=27447)

That's just for changing the speed on the fly. The actual "clock" is listed below at 2793 MHz (fifth from the bottom).

---

### Post by wojox on 2011-02-07
What if you just run:

```
cat /proc/cpuinfo
```

---

### Post by pqwoerituytrueiwoq on 2011-02-07
> **lukeiamyourfather said:**
> Does that processor even have speed stepping? I don't think it does, where it says idle states.

[http://ark.intel.com/Product.aspx?id=27447](http://ark.intel.com/Product.aspx?id=27447)

That's just for changing the speed on the fly. The actual "clock" is listed below at 2793 MHz (fifth from the bottom).
I do not think they put that evil thing (speed step) on desktops
as far as i can tell there is no speed step
hyper threading is disabled (Does the core support this? no) 
cpu speed is normal (other option is compatable)
------------
@wojox
```
~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping    : 9
cpu MHz        : 2793.473
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips    : 5586.94
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:
```

---

### Post by lukeiamyourfather on 2011-02-08
> **pqwoerituytrueiwoq said:**
> I do not think they put that evil thing (speed step) on desktops
as far as i can tell there is no speed step
hyper threading is disabled (Does the core support this? no) 
cpu speed is normal (other option is compatable)
------------
@wojox
```
~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping    : 9
cpu MHz        : 2793.473
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips    : 5586.94
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:
```

What are you asking then? Also dynamic frequency scaling is not evil... :lolflag:

---

### Post by pqwoerituytrueiwoq on 2011-02-08
by evil i mean locking your core speed at 48% :lolflag:
i wanted to be able to get teh applet working so i can see what speed it is working at i do not care about changing the speed just seeing it

---

### Post by lukeiamyourfather on 2011-02-08
> **pqwoerituytrueiwoq said:**
> by evil i mean locking your core speed at 48% :lolflag:
i wanted to be able to get teh applet working so i can see what speed it is working at i do not care about changing the speed just seeing it

You're talking about the little icon in the GNOME panel? From what I can tell it only works if your processor actually has dynamic frequency scaling. Otherwise there's no point because the processor will always be running at the same speed. If you just want to see the speed for shits and giggles then try something like Conky.

---

