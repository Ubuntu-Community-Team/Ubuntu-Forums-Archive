---
title: "How do I tell if I'm using both cpu's"
date: 2010-12-09
forum: General Help
---

### Post by ronnielsen1 on 2010-12-09
I'm working on a Toshiba Magnia 5180 with 2 pentium 3's 733 Mhz. I'm not sure I'm using both of them. How do I find this out?

---

### Post by amauk on 2010-12-09
does the system monitor show both cpus?

---

### Post by I'mGeorge on 2010-12-09
the following commands will show you
```

lscpu
cat /proc/cpuinfo
top (for more hardware info details)

```

---

### Post by ronnielsen1 on 2010-12-09
> ~$ lscpu
Architecture:          i686
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         2
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 8
Stepping:              6
CPU MHz:               733.421



> cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 8
model name    : Pentium III (Coppermine)
stepping    : 6
cpu MHz        : 733.421
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pse36 mmx fxsr sse
bogomips    : 1466.84
clflush size    : 32
cache_alignment    : 32
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 8
model name    : Pentium III (Coppermine)
stepping    : 6
cpu MHz        : 733.421
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pse36 mmx fxsr sse
bogomips    : 1466.83
clflush size    : 32
cache_alignment    : 32
address sizes    : 36 bits physical, 32 bits virtual
power management:


So, I guess that's a yes

---

### Post by I'mGeorge on 2010-12-09
> **ronnielsen1 said:**
> So, I guess that's a yes

yup but it's one of the first intels processors with two cores and it only supports 32 bits

---

### Post by amauk on 2010-12-09
> **I'mGeorge said:**
> yup but it's one of the first intels processors with two cores and it only supports 32 bitsPentium 3 is not a 64bit processor

---

### Post by I'mGeorge on 2010-12-09
> **amauk said:**
> Pentium 3 is not a 64bit processor

that's what I was saying, but as  I've looked closer, it's not one of the first intel dual cores but it's a mainboard with two cpu sockets. I've only looked at the architecture and the number of CPU's, and I've made a little confusion.

Anyway it's not compatible with 64 bit applications.

---

### Post by ronnielsen1 on 2010-12-09
> yup but it's one of the first intels processors with two cores and it only supports 32 bits

yeah but it surprised me running a live cd through it. I thought, wait a minute, pentium 3 shouldn't be this fast

---

### Post by I'mGeorge on 2010-12-09
> **ronnielsen1 said:**
> yeah but it surprised me running a live cd through it. I thought, wait a minute, pentium 3 shouldn't be this fast

I've corrected myself, you have two pentium 3, 733.421 Mhz operational processors installed on your motherboard. It's not a dual core but two PIII processors installed on the same mainboard and they seam very functional 'cause your question was how can you tell if they work.

---

### Post by Decatf on 2010-12-09
Pentium IIIs were excellent processors. They were the basis for the Pentium-M architecture which ultimately became the basis for the Core architecture.

---

