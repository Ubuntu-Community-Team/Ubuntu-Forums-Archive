---
title: "/proc/cpuinfo not showing all 16 cores in 11.10"
date: 2012-02-16
forum: General Help
---

### Post by eprimaveri on 2012-02-16
For some reason /proc/cpuinfo is only displaying one core from a 16 core processor.  However hwinfo --cpu shows the 16 cores.  I have ACPI enable in the bios and I have cleared the noacpi tags out of the grub.cfg file.  Anyone have any ideas out to get this corrected?

System Specs:
SuperMicro AS-1012G-MTF Server
AMD 6274
64GB Memory


/proc/cpuinfo
> processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 1
model name	: AMD Opteron(TM) Processor 6274                 
stepping	: 2
cpu MHz		: 2200.000
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 32
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc up rep_good nopl nonstop_tsc extd_apicid amd_dcm aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bogomips	: 4400.56
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate [9]

hwinfo --cpu
> 01: None 00.0: 10103 CPU                                        
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: X86-64
  Vendor: "AuthenticAMD"
  Model: 21.1.2 "AMD Opteron(TM) Processor 6274                 "
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,pdpe1gb,rdtscp,lm,constant_tsc,up,rep_good,nopl,nonstop_tsc,extd_apicid,amd_dcm,aperfmperf,pni,pclmulqdq,monitor,ssse3,cx16,sse
  Clock: 2200 MHz
  BogoMips: 4400.56
  Cache: 2048 kb
  **[COLOR="Magenta"]Units/Processor: 16[/COLOR]**
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by eprimaveri on 2012-02-17
No one has any ideas they want to throw out?

---

### Post by matt_symes on 2012-02-18
Hi

Are the cores online ? Are they present ?

What's the output of

```
cat /sys/devices/system/cpu/present
```

and

```
cat /sys/devices/system/cpu/online
```

What kernel are you using ?

```
uname -a
```

Kind regards

---

### Post by efflandt on 2012-02-18
**Units/Processor:** is apparently NOT referring to number of cores, because mine also says **16**, but my cpu has 2 cores with hyperthreading, (which appears to be 4 cores to any OS).  And your hwinfo should show "each" core that is available or active.  For example:

```
01: None 00.0: 10103 CPU                                        
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: X86-64
  Vendor: "GenuineIntel"
  Model: 6.37.2 "Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,syscall,nx,rdtscp,lm,constant_tsc,arch_perfmon,pebs,bts,rep_good,nopl,xtopology,nonstop_tsc,aperfmperf,pni,pclmulqdq,dtes64,monitor,ds_
  Clock: 1200 MHz
  BogoMips: 6383.98
  Cache: 4096 kb
  Units/Processor: 16
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 01.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: wkFv.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: X86-64
  Vendor: "GenuineIntel"
  Model: 6.37.2 "Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,syscall,nx,rdtscp,lm,constant_tsc,arch_perfmon,pebs,bts,rep_good,nopl,xtopology,nonstop_tsc,aperfmperf,pni,pclmulqdq,dtes64,monitor,ds_
  Clock: 1200 MHz
  BogoMips: 6383.86
  Cache: 4096 kb
  Units/Processor: 16
  Config Status: cfg=new, avail=yes, need=no, active=unknown

03: None 02.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: +rIN.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: X86-64
  Vendor: "GenuineIntel"
  Model: 6.37.2 "Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,syscall,nx,rdtscp,lm,constant_tsc,arch_perfmon,pebs,bts,rep_good,nopl,xtopology,nonstop_tsc,aperfmperf,pni,pclmulqdq,dtes64,monitor,ds_
  Clock: 1200 MHz
  BogoMips: 6383.85
  Cache: 4096 kb
  Units/Processor: 16
  Config Status: cfg=new, avail=yes, need=no, active=unknown

04: None 03.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: 4zLr.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: X86-64
  Vendor: "GenuineIntel"
  Model: 6.37.2 "Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,syscall,nx,rdtscp,lm,constant_tsc,arch_perfmon,pebs,bts,rep_good,nopl,xtopology,nonstop_tsc,aperfmperf,pni,pclmulqdq,dtes64,monitor,ds_
  Clock: 2933 MHz
  BogoMips: 6383.84
  Cache: 4096 kb
  Units/Processor: 16
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```/proc/cpuinfo shows **cpu cores : 2**, but data for each virtual **processor** (0 thru 3).

Also see what **dmesg** or /var/log/syslog says about your cpu.

---

### Post by dcstar on 2012-02-18
> **eprimaveri said:**
> For some reason /proc/cpuinfo is only displaying one core from a 16 core processor.  However hwinfo --cpu shows the 16 cores.  I have ACPI enable in the bios
.........

[LIST=1]
[*]Don't quote code - "Quote" tags are for what **other** people write.
[*]Check your BIOS and enable **all** CPU resources - only one is detected by your system.
[/LIST]

---

### Post by eprimaveri on 2012-02-20
> **matt_symes said:**
> Hi

Are the cores online ? Are they present ?

What's the output of

```
cat /sys/devices/system/cpu/present
```

and

```
cat /sys/devices/system/cpu/online
```

What kernel are you using ?

```
uname -a
```

Kind regards


cat /sys/devices/system/cpu/present = 0 
cat /sys/devices/system/cpu/online = 0
uname -a = Linux 3.0.0-12-server #20-Ubuntu SMP Fri Oct 7 16:36:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

/var/log/syslog:

powernow-k8: Found 2 AMD Opteron(TM) Processor 6274                  (1 cpu cores) (version 2.20.00)
Feb 20 02:10:25 kernel: [    2.355770] powernow-k8: Core Performance Boosting: on.
Feb 20 02:10:25 kernel: [    2.355843] powernow-k8:    0 : pstate 0 (2200 MHz)
Feb 20 02:10:25 kernel: [    2.355849] powernow-k8:    1 : pstate 1 (2000 MHz)
Feb 20 02:10:25 kernel: [    2.355855] powernow-k8:    2 : pstate 2 (1800 MHz)
Feb 20 02:10:25 kernel: [    2.355860] powernow-k8:    3 : pstate 3 (1600 MHz)
Feb 20 02:10:25 kernel: [    2.355865] powernow-k8:    4 : pstate 4 (1400 MHz)

I had to disable "apic support" in the BIOS just to get the installer and server to load.

From what I can tell all cores are enabled in the BIOS.

Thanks for the help!

---

### Post by matt_symes on 2012-02-20
Hi

As dcstar pointed and those commands verified, you only have one CPU that is recognised let alone online.

Are you sure your BIOS is setup correctly ? I would triple check that.

In the meantime, boot your PC and then when booted post the output of..

```
grep -i cpu /var/log/kern.log
```

Kind regards

---

### Post by eprimaveri on 2012-02-20
> **matt_symes said:**
> Hi

As dcstar pointed and those commands verified, you only have one CPU that is recognised let alone online.

Are you sure your BIOS is setup correctly ? I would triple check that.

In the meantime, boot your PC and then when booted post the output of..

```
grep -i cpu /var/log/kern.log
```

Kind regards

I have checked the BIOS once agin and it looks correct.  Here is what the log has.

```

Feb 20 12:10:33 node22 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 20 12:10:33 node22 kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 20 12:10:33 node22 kernel: [    0.000000] KERNEL supported cpus:
Feb 20 12:10:33 node22 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 20 12:10:33 node22 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Feb 20 12:10:33 node22 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:1 nr_node_ids:2
Feb 20 12:10:33 node22 kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88081fc00000 s79616 r8192 d22784 u2097152
Feb 20 12:10:33 node22 kernel: [    0.000000] pcpu-alloc: s79616 r8192 d22784 u2097152 alloc=1*2097152
Feb 20 12:10:33 node22 kernel: [    0.000000] pcpu-alloc: [0] 0 
Feb 20 12:10:33 node22 kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=2
Feb 20 12:10:33 node22 kernel: [    0.057858] Initializing cgroup subsys cpuacct
Feb 20 12:10:33 node22 kernel: [    0.057943] CPU: Physical Processor ID: 0
Feb 20 12:10:33 node22 kernel: [    0.057947] CPU: Processor Core ID: 0
Feb 20 12:10:33 node22 kernel: [    0.057951] mce: CPU supports 7 MCE banks
Feb 20 12:10:33 node22 kernel: [    0.072077] weird, boot CPU (#32) not listed by the BIOS.
Feb 20 12:10:33 node22 kernel: [    0.076004] Brought up 1 CPUs
Feb 20 12:10:33 node22 kernel: [    0.187050] Switched to NOHz mode on CPU #0
Feb 20 12:10:33 node22 kernel: [    1.684603] ACPI: acpi_idle registered with cpuidle
Feb 20 12:10:33 node22 kernel: [    2.183587] cpuidle: using governor ladder
Feb 20 12:10:33 node22 kernel: [    2.183592] cpuidle: using governor menu
Feb 20 12:10:33 node22 kernel: [    2.340316] powernow-k8: Found 2 AMD Opteron(TM) Processor 6274                  (1 cpu cores) (version 2.20.00)

```

---

### Post by matt_symes on 2012-02-21
Hi

> ...
SMP: Allowing 1 CPUs, 0 hotplug CPUs
...
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
...

It's only allowing one core.

Let's see what your BIOS thinks. Run this command and post back the results.

```
sudo dmidecode -t processor
```

If you need to install dmidecode run this.

```
sudo apt-get install dmidecode
```

EDIT:

Can you also please post the output of

```
cat /proc/cmdline
```

Kind regards

---

### Post by Crinos512 on 2012-02-22
Having similar issues here with my quad core Phenom. It was working fine with all 4 cores until I did a reinstall of Kubuntu... now just 1 core shows up.

Attaching results that may be helpful:
```

crinos@Fortress:~$ cat /proc/cpuinfo
[COLOR="Red"]processor       : 0[/COLOR]
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 4
model name      : AMD Phenom(tm) II X4 820 Processor
stepping        : 2
cpu MHz         : 2800.309
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
bogomips        : 5600.61
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

``````

crinos@Fortress:~$ hwinfo --cpu
[COLOR="Red"]01:[/COLOR] None 00.0: 10103 CPU                                        
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: X86-64
  Vendor: "AuthenticAMD"
  Model: 16.4.2 "AMD Phenom(tm) II X4 820 Processor"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,pdpe1gb,rdtscp,lm,3dnowext,3dnow,constant_tsc,rep_good,nopl,nonstop_tsc,pni,monitor,cx16,popcnt,lahf_lm,cmp_legacy,svm,extapic,cr8_l
  Clock: 2800 MHz
  BogoMips: 5600.61
  Cache: 512 kb
  Units/Processor: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

``````

crinos@Fortress:~$ cat /sys/devices/system/cpu/present
[COLOR="red"]0[/COLOR]

``````

crinos@Fortress:~$ cat /sys/devices/system/cpu/online
[COLOR="red"]0[/COLOR]

``````

crinos@Fortress:~$ grep -i cpu /var/log/kern.log
Feb 20 10:26:35 Fortress kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 20 10:26:35 Fortress kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 20 10:26:35 Fortress kernel: [    0.000000] KERNEL supported cpus:
Feb 20 10:26:35 Fortress kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 20 10:26:35 Fortress kernel: [    0.000000] Processor #0 (Bootup-CPU)
Feb 20 10:26:35 Fortress kernel: [    0.000000] SMP: [COLOR="red"]Allowing 4 CPUs[/COLOR], 0 hotplug CPUs
Feb 20 10:26:35 Fortress kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Feb 20 10:26:35 Fortress kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88022fc00000 s79616 r8192 d22784 u524288
Feb 20 10:26:35 Fortress kernel: [    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
Feb 20 10:26:35 Fortress kernel: [    0.000000] [COLOR="red"]pcpu-alloc: [0] 0 1 2 3[/COLOR] 
Feb 20 10:26:35 Fortress kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Feb 20 10:26:35 Fortress kernel: [    0.010810] Initializing cgroup subsys cpuacct
Feb 20 10:26:35 Fortress kernel: [    0.010867] CPU: Physical Processor ID: 0
Feb 20 10:26:35 Fortress kernel: [    0.010868] CPU: Processor Core ID: 0
Feb 20 10:26:35 Fortress kernel: [    0.010870] mce: CPU supports 6 MCE banks
Feb 20 10:26:35 Fortress kernel: [    0.016404] [COLOR="red"]Brought up 1 CPUs[/COLOR]
Feb 20 10:26:35 Fortress kernel: [    0.776546] cpuidle: using governor ladder
Feb 20 10:26:35 Fortress kernel: [    0.776546] cpuidle: using governor menu
Feb 20 10:26:35 Fortress kernel: [    0.789877] [COLOR="red"]powernow-k8: Found 1 AMD Phenom(tm) II X4 820 Processor (1 cpu cores) (version 2.20.00)[/COLOR]
Feb 21 18:05:18 Fortress kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 21 18:05:18 Fortress kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 21 18:05:18 Fortress kernel: [    0.000000] KERNEL supported cpus:
Feb 21 18:05:18 Fortress kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 21 18:05:18 Fortress kernel: [    0.000000] Processor #0 (Bootup-CPU)
Feb 21 18:05:18 Fortress kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Feb 21 18:05:18 Fortress kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Feb 21 18:05:18 Fortress kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88022fc00000 s79616 r8192 d22784 u524288
Feb 21 18:05:18 Fortress kernel: [    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
Feb 21 18:05:18 Fortress kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Feb 21 18:05:18 Fortress kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Feb 21 18:05:18 Fortress kernel: [    0.010790] Initializing cgroup subsys cpuacct
Feb 21 18:05:18 Fortress kernel: [    0.010847] CPU: Physical Processor ID: 0
Feb 21 18:05:18 Fortress kernel: [    0.010849] CPU: Processor Core ID: 0
Feb 21 18:05:18 Fortress kernel: [    0.010851] mce: CPU supports 6 MCE banks
Feb 21 18:05:18 Fortress kernel: [    0.016405] Brought up 1 CPUs
Feb 21 18:05:18 Fortress kernel: [    0.776549] cpuidle: using governor ladder
Feb 21 18:05:18 Fortress kernel: [    0.776549] cpuidle: using governor menu
Feb 21 18:05:18 Fortress kernel: [    0.789876] powernow-k8: Found 1 AMD Phenom(tm) II X4 820 Processor (1 cpu cores) (version 2.20.00)

``````

crinos@Fortress:~$ sudo dmidecode -t processor
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0004, DMI type 4, 42 bytes
Processor Information
        Socket Designation: CPU 1
        Type: Central Processor
        Family: <OUT OF SPEC>
        Manufacturer: AMD              
        ID: 42 0F 10 00 FF FB 8B 17
        Version: AMD Phenom(tm) II X4 820 Processor                  
        Voltage: 1.5 V
        External Clock: 200 MHz
        Max Speed: 2800 MHz
        Current Speed: 2800 MHz
        Status: Populated, Enabled
        Upgrade: Other
        L1 Cache Handle: 0x0005
        L2 Cache Handle: 0x0006
        L3 Cache Handle: 0x0007
        Serial Number:  
        Asset Tag:  
        Part Number:  
        [COLOR="Red"]Core Count: 4
        Core Enabled: 4[/COLOR]
        Characteristics:
                64-bit capable

``````

crinos@Fortress:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=4e7d1537-4ed2-4207-b222-3b4dcac5d7e9 ro acpi=off noapic nolapic nodmraid quiet splash vt.handoff=7

```

---

### Post by dcstar on 2012-02-22
> **eprimaveri said:**
> 
........
I had to disable "**apic** support" in the BIOS just to get the installer and server to load.


That is what allows multi-CPUs to work!

No APIC = one CPU.

---

### Post by matt_symes on 2012-02-22
Hi

> **dcstar said:**
> That is what allows multi-CPUs to work!

No APIC = one CPU.

Beaten to it :D This is an ACPI issue.

acpi=off and noapic are blunt instruments. You can get finer control than that.

What exactly was causing your PC not to boot ? Was this just a "add a kernel command line option and hope" ?

Kind regards

---

### Post by dcstar on 2012-02-22
> **matt_symes said:**
> hi



beaten to it :d this is an acpi issue.

Acpi=off and noapic are blunt instruments. You can get finer control than that.


apic <> apci.

---

### Post by matt_symes on 2012-02-22
Hi

> **dcstar said:**
> apic <> apci.

I know :) 

I think the posters need to find out why they think they needed these switches in the command line to make the system boot.

> <kernel cmd line snip> ... acpi=off noapic nolapic ...

That has turned off a lot of functionality in the kernel. I would be surprised if all those switches were required to make the system boot.

Kind regards

---

### Post by Crinos512 on 2012-02-22
So if I change my Boot args from 
```

ro [COLOR="Red"]acpi=off noapic nolapic[/COLOR] nodmraid quiet splash vt.handoff=7

```
to
```

ro nodmraid quiet splash vt.handoff=7

```

I should be fine?

---

### Post by Crinos512 on 2012-02-22
Yep, That did it. :D 

...Happy now. Thanks! :popcorn:

---

### Post by dcstar on 2012-02-23
> **matt_symes said:**
> 
I think the posters need to find out why they think they needed these switches in the command line to make the system boot.


Probably because they "saw it on a web site" and follow totally inappropriate instructions because they have little or no clue as to actually what they are doing.

---

### Post by Crinos512 on 2012-02-24
> **dcstar said:**
> Probably because they "saw it on a web site" and follow totally inappropriate instructions because they have little or no clue as to actually what they are doing.

Well, I can't speak to everyone who may have had this issue. but I've always had to use the "Alternate" install disc on this system before. When I did my reinstall recently I went to get the iso from [http://cdimage.ubuntu.com/kubuntu/oneiric/]("http://cdimage.ubuntu.com/kubuntu/oneiric/") and noticed there was no Alternate ISO.

I was able to use the normal ISO and install completely by altering some of the livedisc's boot parameters... but I didn't realize that those parameters would be set on the finalized install as well.

I may have just enough of a clue to cause myself problems, but I can usually noodle it out with a little research and help from a patient community. I haven't considered myself Clueless on linux for a few years now, but there are parts of the system I haven't messed with much.

I guess what I'm trying to say is thanks for the humility check, but don't be so hard on Noobs... they will be the Sages that others will turn to some day.

---

