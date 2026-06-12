---
title: "64bit or 32 bit"
date: 2010-08-04
forum: General Help
---

### Post by rob_38 on 2010-08-04
how can I tell if my cpu is 64 or 32 bit?

I have 4gb of ram chips in there but only 3gb (ish) is showing

---

### Post by realzippy on 2010-08-04
If you do not know which cpu you  are using,open a terminal:

```
cat /proc/cpuinfo
```


If you run a 64bit cpu with a 32 bit OS the whole 4 GB will also not recognized fully.

---

### Post by rob_38 on 2010-08-04
rob@desktop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping    : 10
cpu MHz        : 2003.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 6000.56
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping    : 10
cpu MHz        : 2003.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips    : 5999.94
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by Zorgoth on 2010-08-04
Type "uname -m" to check if the Ubuntu you are running is 32 or 64-bit.

It will do something like i386 or i686 if it is 32-bit, and x86_64 if it is 64-bit.

As for your *processor*, just google it or tell us the name of it.

EDIT:  That is a 64-bit cpu.

---

### Post by realzippy on 2010-08-04
Intel(R) Core(TM)2 Duo CPU E8400


is a 64 Bit cpu.

---

### Post by rob_38 on 2010-08-04
is it worth upgrading to 64bit 10.04?

---

### Post by realzippy on 2010-08-04
It does no harm and your RAM will be recognized fully.
If you do not run huge applications at the same time (e.g. video encoding/audio transcoding) you probably will not notice an improvement of speed...

BTW:

[http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by rob_38 on 2010-08-04
i've been meaning to use ardour.

will my motherboard handle more ram?

---

### Post by realzippy on 2010-08-04
*will my motherboard handle more ram?*


you mean physically?
Depends on the mainboard..

---

### Post by rob_38 on 2010-08-04
Yeah, I always thought I had a 32 bit cpu until now. 

Wouldn't mind getting all my 4gb working + overclock haha.

---

### Post by realzippy on 2010-08-04
[http://ardour.org/node/142](http://ardour.org/node/142)

Overclock?
In the moment you underclock.Your CPU runs at 2 GHz due to energy savings
enabled..   ;-)

Fun aside,
go with 64 bit to recognize your full 4 GB RAM

---

### Post by FahadMKS on 2010-08-04
> **Zorgoth said:**
> Type "uname -m" to check if the Ubuntu you are running is 32 or 64-bit.

It will do something like i386 or i686 if it is 32-bit, and x86_64 if it is 64-bit.

As for your *processor*, just google it or tell us the name of it.

EDIT:  That is a 64-bit cpu.


This command is Simpler than the above one and gives the correct Info

---

### Post by realzippy on 2010-08-04
Two totally different commands cannot be compared.One is for cpu,the other for the os  ;)

---

### Post by oldos2er on 2010-08-04
> **rob_38 said:**
> is it worth upgrading to 64bit 10.04?

There's no upgrade, you'll need to do a fresh install.

---

