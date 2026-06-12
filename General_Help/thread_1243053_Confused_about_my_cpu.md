---
title: "Confused about my cpu"
date: 2009-08-17
forum: General Help
---

### Post by Nugar on 2009-08-17
Hi all,

I apologize if this topic is not appropriate for this section.

Some time ago, I installed an info screenlet, more precisely "Sysmonitor". It shows two cpus, but as far as I know, I only have one single core 3GHz Pentium 4 chip.

When I run: 

```
cat /proc/cpuinfo
```I get this:

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 5
cpu MHz        : 2400.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est tm2 cid cx16 xtpr pdcm lahf_lm
bogomips    : 5984.54
clflush size    : 64
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 6
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 5
cpu MHz        : 2400.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est tm2 cid cx16 xtpr pdcm lahf_lm
bogomips    : 5985.48
clflush size    : 64
power management:

```

Why is this? Do I (unknowingly) have a dual core cpu?

I'm running Ubuntu 9.04

Thanks in advance,

---

### Post by wojox on 2009-08-17
Yes you unknowingly do.

---

### Post by Whiffle on 2009-08-17
I think you have a CPU that supports Hyperthreading, which is some kind of pseudo-2-cpu thing Intel did for a while, and causes your CPU to show up as 2 cpu's instead.

---

### Post by Nugar on 2009-08-17
@wojox:

No disrespect, but...

Are you kidding me? Or is it really a dual core cpu? It was sold to me as single core, IIRC.

@Whiffle:

Sounds logical, how do I find out?

Cheers,

---

### Post by lensman3 on 2009-08-17
Run from a command line:

dmesg | more

just after you reboot.  You will see the Linux OS sort out the various CPU's.

Hope this helps.

---

### Post by raymondh on 2009-08-17
> **Whiffle said:**
> I think you have a CPU that supports Hyperthreading, which is some kind of pseudo-2-cpu thing Intel did for a while, and causes your CPU to show up as 2 cpu's instead.

+1 ... [hyperthreading]("http://en.wikipedia.org/wiki/Hyper-threading") to improve parralelization.

---

### Post by Whiffle on 2009-08-17
> **Nugar said:**
> 

@Whiffle:

Sounds logical, how do I find out?

Cheers,


You have the "ht" flag in the flags section of your cpuinfo.

---

### Post by Nugar on 2009-08-17
Ok, just for the sake of not rebooting, I ran the command and got this (snipped):

```
[    0.004305] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004308] CPU: L2 cache: 2048K
[    0.004312] CPU: Physical Processor ID: 0
[    0.004314] CPU: Processor Core ID: 0
[    0.004320] using mwait in idle threads.
[    0.004334] Checking 'hlt' instruction... OK.
[    0.023597] ACPI: Core revision 20080926
[    0.026408] ACPI: Checking initramfs for custom DSDT
[    0.320518] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.360207] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[    0.364001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5985.48 BogoMIPS (lpj=11970962)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.452571] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[    0.452599] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.456056] Brought up 2 CPUs
[    0.456062] Total of 2 processors activated (11970.02 BogoMIPS).
[    0.456136] CPU0 attaching sched-domain:
[    0.456140]  domain 0: span 0-1 level SIBLING
[    0.456143]   groups: 0 1
[    0.456151] CPU1 attaching sched-domain:
[    0.456154]  domain 0: span 0-1 level SIBLING
[    0.456157]   groups: 1 0
[    0.456249] net_namespace: 776 bytes

```

What does it say? I can't understand that...

---

### Post by JKyleOKC on 2009-08-17
Look closely at the "flags" line of your original cpuid results: it includes "ht" which indicates that while your cpu is indeed single core, it includes the hyperthreading feature which is a sort of imitation dual core. I have the exact same situation here, and my VMWare server installation recognizes the host CPU as having two cores even though it actually has only one -- and as a consequence, when things are really loading down the system, I can see "130%" CPU usage reported!

While I don't know all the details of how the ht feature works, I suspect it's by means of something called "pipeline overlap" which allows the CPU to process one instruction while fetching one or more subsequent ones, thus making it faster than it would be without the overlap.

At any rate, no need to be alarmed about it; consider it an added bonus!

---

### Post by Nugar on 2009-08-17
Thanks guys!

Cheers,

---

### Post by wojox on 2009-08-17
Oops, sorry about that. I look at Processor 0 & Processor 1 and figured two processors. Never looked for a hyper-threading flag.

---

