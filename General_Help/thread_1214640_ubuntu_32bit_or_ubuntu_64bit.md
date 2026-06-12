---
title: "ubuntu 32bit or ubuntu 64bit"
date: 2009-07-16
forum: General Help
---

### Post by tcpa41 on 2009-07-16
Hello boys and gals :) . Currently im running 32bit ubuntu on crappy 1,6Ghz  amd sempron 2800+ palermo core.Recently while reading one blog i stumbled upon an interesting thing which sayd if in cpu flags you have lm flags you can run 64bit os on it. 
Well i ran cat/proc/cpuinfo and thats the output I've got:
```

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 44
model name    : AMD Sempron(tm) Processor 2800+
stepping    : 2
cpu MHz        : 1600.023
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips    : 3200.04
clflush size    : 64
power management: ts ttp tm stc

```

As you can see in "flags:" lm flag is present,does that mean that i can successfully run 64bit ubuntu on my pc?

---

