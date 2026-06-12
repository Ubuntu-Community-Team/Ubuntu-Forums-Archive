---
title: "Why do I get different information about my cpu??"
date: 2011-07-08
forum: General Help
---

### Post by ClientAlive on 2011-07-08
I'm wondering why I'm getting different information about my cpu from different sources within Ubuntu? Is it giving different units of measure or something? But both say MHz.

```

**:~$ cat /proc/cpuinfo**
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 36
model name	: AMD Turion(tm) 64 Mobile Technology ML-34
stepping	: 2
**cpu MHz	: 800.000**
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips	: 1595.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```


```

**:~$ lshw**
WARNING: you should run this program as super-user.
bashbox                   
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: AMD Turion(tm) 64 Mobile Technology ML-34
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.4.2
          **size: 1800MHz**
          **capacity: 1800MHz**
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq

```

---

### Post by dcstar on 2011-07-08
> **ClientAlive said:**
> I'm wondering why I'm getting different information about my cpu from different sources within Ubuntu? Is it giving different units of measure or something? But both say MHz.
........

One tells you what it is doing **now** and the other tells you what it is capable of.

---

### Post by ClientAlive on 2011-07-08
> **dcstar said:**
> One tells you what it is doing **now** and the other tells you what it is capable of.

Ahh . . .  I see . . .

So I assume it's the

```
lshw
```

that's telling me "what it's capable of"?


Thanks

---

