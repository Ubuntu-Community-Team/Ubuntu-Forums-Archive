---
title: "SMP not working - only 1 core is visible!"
date: 2011-11-09
forum: General Help
---

### Post by torsionbar on 2011-11-09
Hello all,

I'm running 11.04 on an AMD Opteron 1218 HE dual core processor.  When I first installed it, I remember looking at  /proc/cpuinfo and seeing 2 cores.  Good.  Recently things were running slow, and I just happened to take a peek at /proc/cpuinfo and now I only see one core!  I also see some lines from dmesg showing that only 1 core is being utilized.  There have been several kernel updates since I first installed 11.04 (I'm all patched up to date) so I'm wondering if one of those updates broke SMP on AMD64??

Any ideas?  Thanks everyone.


[FONT=Courier New][SIZE=2]$ uname -a
Linux nostromo 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:27:32 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 67
model name    : Dual-Core AMD Opteron(tm) Processor 1218 HE
stepping    : 3
cpu MHz        : 1000.000
cache size    : 1024 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips    : 2010.19
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc[/SIZE][/FONT]

interesting lines from "dmesg" command:
[FONT=Courier New][SIZE=2]
[    0.017072] CPU: Physical Processor ID: 0
[    0.017074] CPU: Processor Core ID: 0
[    0.017076] mce: CPU supports 5 MCE banks
[    0.017085] using C1E aware idle routine
[    0.017106] SMP alternatives: switching to UP code
[    0.024775] Freeing SMP alternatives: 20k freed
...
[    0.030077] weird, boot CPU (#0) not listed by the BIOS.
[    0.030080] SMP motherboard not detected.
[    0.030086] Setting APIC routing to flat
[    0.040000] SMP disabled
...
[    0.040000] Brought up 1 CPUs
[    0.040000] Total of 1 processors activated (5226.51 BogoMIPS).[/SIZE][/FONT]

---

### Post by torsionbar on 2011-11-09
Ok, looks like I solved it.  That was quick, lol.

I rebooted and went into the BIOS settings.  Two things jumped out at me.  IOAPIC was disabled, and the year was 2099.

I enabled IOAPIC and corrected the year to 2011.  Then I booted the OS and it sees both cores again now.

Easy fix!

[FONT=Courier New][SIZE=2]$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 67
model name    : Dual-Core AMD Opteron(tm) Processor 1218 HE
stepping    : 3
cpu MHz        : 2600.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips    : 5226.46
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 67
model name    : Dual-Core AMD Opteron(tm) Processor 1218 HE
stepping    : 3
cpu MHz        : 2600.000
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips    : 5226.46
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc[/SIZE][/FONT]

---

### Post by dcstar on 2011-11-10
> **torsionbar said:**
> Ok, looks like I solved it.  That was quick, lol.

I rebooted and went into the BIOS settings.  Two things jumped out at me.  IOAPIC was disabled, and the year was 2099.

........

You may want to replace the motherboard battery.

---

