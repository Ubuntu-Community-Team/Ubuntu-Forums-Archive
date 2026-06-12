---
title: "is my cpu capable of 64bit processing?"
date: 2009-09-24
forum: General Help
---

### Post by renkinjutsu on 2009-09-24
hmm ..
lshw:
(scroll to right)
```
  *-cpu
       product: Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.7.6
       serial: 0001-0676-0000-0000-0000-0000
       size: 2534MHz
       capacity: 2534MHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **x86-64** constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm cpufreq
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 64 bits
          capabilities: logical
```

but ```
uname -m
i686
```

?

---

### Post by gordintoronto on 2009-09-24
Yes, it is 64-bit capable.

---

### Post by QIII on 2009-09-24
CPU - Yes.

Are you currently running a 32 bit version?
 
There is something interesting with uname.  According to the man pages, the -m switch should give you the machine architecture.  Apparently, however, some Linux distros give back the machine architecture for which the current OS is targeted. 

I haven't been able to confirm that rumor...

But yes.  Your Core2 Duo is definitely a 64 bit processor.

---

### Post by renkinjutsu on 2009-09-24
i don't think it's showing the arch of my OS, because i thought Ubuntu built i386 binaries?

---

### Post by dcstar on 2009-09-25
> **renkinjutsu said:**
> i don't think it's showing the arch of my OS, because i thought Ubuntu built i386 binaries?

Download the 64-bit version, it is clearly offered in the appropriate section of the Ubuntu website.

---

