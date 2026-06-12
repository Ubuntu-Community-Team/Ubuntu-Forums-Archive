---
title: "athlon 64 x2 multicore second core doesn't show up in 10.10 maverick"
date: 2010-11-20
forum: General Help
---

### Post by *yH&gt;jw+o! on 2010-11-20
any ideas
uname -a
```

Linux BOX 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

```

cat /proc/cpuid
```

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 43
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping    : 1
cpu MHz        : 2000.000
cache size    : 512 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good extd_apicid pni lahf_lm cmp_legacy
bogomips    : 4666.15
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```

dmesg |grep -i cpu
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u2097152
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.022760] Initializing cgroup subsys cpuacct
[    0.022822] CPU: Physical Processor ID: 0
[    0.022823] CPU: Processor Core ID: 0
[    0.022826] mce: CPU supports 5 MCE banks
[    0.046908] weird, boot CPU (#0) not listed by the BIOS.
[    0.050000] Brought up 1 CPUs
[    0.175086] ACPI: acpi_idle registered with cpuidle
[    0.241360] cpuidle: using governor ladder
[    0.241364] cpuidle: using governor menu
[    0.242415] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (1 cpu cores) (version 2.20.00)
[   82.270192] Marking TSC unstable due to cpufreq changes

```

I've turned off most acpi features in bios....and no answer was otherwise found from googling....

now what

---

### Post by Artemis3 on 2010-11-21
Double check your bios options, and turn the acpi things back on...

---

### Post by Edglex on 2011-08-18
I have the same problem in all versions of ubuntu I have tried (11.04, 10.10, 10.04). Did you find any solution?

---

