---
title: "Enabling hyperthreading"
date: 2011-09-08
forum: General Help
---

### Post by jcredberry on 2011-09-08
Dear all. I have Natty 64-bit installed in a computer with an Intel Xeon Processor W3530 (Quad Core, Hyperthreading). I checked and both, System Monitor and Top show only four processors, meaning that hyperthreading is not enabled. Can somebody explain to me how to enable it?

Thanks in advance. Best regards.

---

### Post by haqking on 2011-09-08
> **jcredberry said:**
> Dear all. I have Natty 64-bit installed in a computer with an Intel Xeon Processor W3530 (Quad Core, Hyperthreading). I checked and both, System Monitor and Top show only four processors, meaning that hyperthreading is not enabled. Can somebody explain to me how to enable it?

Thanks in advance. Best regards.


can you post the ouput of following:

dmesg | grep CPU

i thought the kernel detected it automatically

and is it enabled in BIOS ?

---

### Post by jcredberry on 2011-09-08
Sure:
```
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0400, DMI type 4, 40 bytes
Processor Information
	Socket Designation: CPU
	Type: Central Processor
	Family: Xeon
	Manufacturer: Intel
	ID: A5 06 01 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 26, Stepping 5
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Not Specified
	Voltage: Unknown
	External Clock: 4800 MHz
	Max Speed: 3800 MHz
	Current Speed: 2800 MHz
	Status: Populated, Enabled
	Upgrade: Socket LGA771
	L1 Cache Handle: 0x0700
	L2 Cache Handle: 0x0701
	L3 Cache Handle: 0x0704
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Core Count: 4
	Core Enabled: 4
	Thread Count: 2
	Characteristics:
		64-bit capable

jcredberry@2e14-200305:~$ sudo dmidecode -t 4|grep HT
		HTT (Hyper-threading technology)
jcredberry@2e14-200305:~$ dmesg | grep CPU
[    0.000000] SMP: Allowing 32 CPUs, 28 hotplug CPUs
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:32 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800df800000 s84416 r8192 d22080 u131072
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=32, Nodes=1
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.003011] CPU: Physical Processor ID: 0
[    0.003012] CPU: Processor Core ID: 0
[    0.003017] mce: CPU supports 9 MCE banks
[    0.003025] CPU0: Thermal monitoring enabled (TM1)
[    0.248693] CPU0: Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz stepping 05
[    0.907367] Brought up 4 CPUs
[    2.154762] Switched to NOHz mode on CPU #0
[    2.154829] Switched to NOHz mode on CPU #2
[    2.154855] Switched to NOHz mode on CPU #1
[    2.154901] Switched to NOHz mode on CPU #3

```

---

### Post by haqking on 2011-09-08
> **jcredberry said:**
> Sure:
```
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0400, DMI type 4, 40 bytes
Processor Information
    Socket Designation: CPU
    Type: Central Processor
    Family: Xeon
    Manufacturer: Intel
    ID: A5 06 01 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 26, Stepping 5
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Hyper-threading technology)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Not Specified
    Voltage: Unknown
    External Clock: 4800 MHz
    Max Speed: 3800 MHz
    Current Speed: 2800 MHz
    Status: Populated, Enabled
    Upgrade: Socket LGA771
    L1 Cache Handle: 0x0700
    L2 Cache Handle: 0x0701
    L3 Cache Handle: 0x0704
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Core Count: 4
    Core Enabled: 4
    Thread Count: 2
    Characteristics:
        64-bit capable

jcredberry@2e14-200305:~$ sudo dmidecode -t 4|grep HT
        HTT (Hyper-threading technology)
jcredberry@2e14-200305:~$ dmesg | grep CPU
[    0.000000] SMP: Allowing 32 CPUs, 28 hotplug CPUs
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:32 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800df800000 s84416 r8192 d22080 u131072
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=32, Nodes=1
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.003011] CPU: Physical Processor ID: 0
[    0.003012] CPU: Processor Core ID: 0
[    0.003017] mce: CPU supports 9 MCE banks
[    0.003025] CPU0: Thermal monitoring enabled (TM1)
[    0.248693] CPU0: Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz stepping 05
[    0.907367] Brought up 4 CPUs
[    2.154762] Switched to NOHz mode on CPU #0
[    2.154829] Switched to NOHz mode on CPU #2
[    2.154855] Switched to NOHz mode on CPU #1
[    2.154901] Switched to NOHz mode on CPU #3

```


It looks enabled to me, one more:

 **cat /proc/cpuinfo**

---

### Post by jcredberry on 2011-09-08
Here (I still believe it is not):
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz
stepping	: 5
cpu MHz		: 2800.305
cache size	: 8192 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5600.61
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz
stepping	: 5
cpu MHz		: 2800.305
cache size	: 8192 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5599.81
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz
stepping	: 5
cpu MHz		: 2800.305
cache size	: 8192 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 4
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5599.81
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz
stepping	: 5
cpu MHz		: 2800.305
cache size	: 8192 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 6
initial apicid	: 6
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5599.81
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

---

### Post by haqking on 2011-09-08
> **jcredberry said:**
> Here (I still believe it is not):
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 26
model name    : Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz
stepping    : 5
cpu MHz        : 2800.305
cache size    : 8192 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5600.61
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 26
model name    : Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz
stepping    : 5
cpu MHz        : 2800.305
cache size    : 8192 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5599.81
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 26
model name    : Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz
stepping    : 5
cpu MHz        : 2800.305
cache size    : 8192 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5599.81
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 26
model name    : Intel(R) Xeon(R) CPU           W3530  @ 2.80GHz
stepping    : 5
cpu MHz        : 2800.305
cache size    : 8192 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5599.81
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

your flags section indicates it is:

flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss [COLOR=Blue]ht
[COLOR=Black]
why do you think it isnt ?

is it set in your BIOS ?

like i said flag is set to should be
[/COLOR][/COLOR]

---

### Post by jcredberry on 2011-09-08
Thanks, but it still doesn't appear in System Monitor or Top. Only four processors, no more. Any idea?

---

### Post by haqking on 2011-09-08
> **jcredberry said:**
> Thanks, but it still doesn't appear in System Monitor or Top. Only four processors, no more. Any idea?


you have a quad core dont you ?

that is 4.

HT is the ability for the cpu to use virtual processors to carry out parallel computations (more than one thread)

I dont think the virtual processors show as extra ?

---

### Post by jcredberry on 2011-09-08
At least in Windows is does so, as well as on previous versions of Ubuntu. See this thread:
[http://ubuntuforums.org/showthread.php?t=1683384](http://ubuntuforums.org/showthread.php?t=1683384)

---

### Post by haqking on 2011-09-08
> **jcredberry said:**
> At least in Windows is does so, as well as on previous versions of Ubuntu. See this thread:
[http://ubuntuforums.org/showthread.php?t=1683384](http://ubuntuforums.org/showthread.php?t=1683384)


mmm i am a bit confused.  The flag is set for HT.  However the siblings value is the same as the core value for you which i think the sibling value should be double ?

LIke i said is HT enabled in your BIOS ?

also is acpi=ht in your grub ?

---

### Post by jcredberry on 2011-09-08
How can I check grub's configuration? As for the moment I cannot reboot to check the BIOS, but I believe that the first time I booted on Windows 7 I saw 8 threads.

---

### Post by gsgleason on 2011-09-08
It has to be enabled in your bios.  Don't bother with any thing else until you check that.

---

### Post by Bodsda on 2011-09-08
> **jcredberry said:**
> How can I check grub's configuration? As for the moment I cannot reboot to check the BIOS, but I believe that the first time I booted on Windows 7 I saw 8 threads.
 
Ignore me, I can't read
 
Bodsda

---

### Post by Manyette on 2011-09-08
As an aside, I have a quad core (I7) and system monitor does show 8 processors bedcause of the HT. Also show 8 cpu's on the system monitor "system" page.

---

### Post by haqking on 2011-09-08
> **Bodsda said:**
> GRUB doesnt have anything to do with the bios or hyper threading. The only way to see if it is enabled as far as I know is to reboot and check your bios.
 
Bodsda
acpi=ht can be set in grub which is why i referred him to it.

[https://wiki.ubuntu.com/DebuggingKernelBoot](https://wiki.ubuntu.com/DebuggingKernelBoot)

and the parameter here [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

---

### Post by haqking on 2011-09-08
> **jcredberry said:**
> How can I check grub's configuration? As for the moment I cannot reboot to check the BIOS, but I believe that the first time I booted on Windows 7 I saw 8 threads.


if it is in Windows then should be enabled in BIOS ?, so aside from the acpi-HT in your grub the only other thing i can think of is your kernel doesnt support it ?

But i doubt it, as it should

---

### Post by jcredberry on 2011-09-08
So Haqking, do I have to reboot to configure grub accordingly? There is no file to change to make it permanent?
Thanx.

---

### Post by Grenage on 2011-09-08
Whoa, Nelly; wasn't the grub ht stuff required years ago when HT was disabled by default, due to performance issues?  It should not be a factor now.

---

### Post by haqking on 2011-09-08
> **Grenage said:**
> Whoa, Nelly; wasn't the grub ht stuff required years ago when HT was disabled by default, due to performance issues?  It should not be a factor now.


yes, it should be enabled by default in the kernel and linux should just see it.

Thats the problem im just stabbing in the dark with his issue, due to it being seen in Windows, enabled in BIOS needs to be checked though and the Flags set from cpuinfo

so i was just throwing it out there ;-)

---

### Post by Grenage on 2011-09-08
> **haqking said:**
> yes, it should be enabled by default in the kernel and linux should just see it.

Thats the problem im just stabbing in the dark with his issue, due to it being seen in Windows, enabled in BIOS obvioulsy and the Flags set from cpuinfo

so i was just throwing it out there ;-)

Sometimes you have to, to get anywhere. :)  Has the OP considered booting from a LiveCD, to see if the problem persists?

---

### Post by haqking on 2011-09-08
> **Grenage said:**
> Sometimes you have to, to get anywhere. :)  Has the OP considered booting from a LiveCD, to see if the problem persists?


not sure yet. I dont think he can reboot for some reason ?

---

### Post by Grenage on 2011-09-08
> **haqking said:**
> not sure yet. I dont think he can reboot for some reason ?

Ah; production server, I guess.

---

### Post by jcredberry on 2011-09-08
I will, only I cannot boot at this moment. Running some program to test the multicore version of some calculations. So far, so good, so I wanted to test it with all 8 threads. Then I found this problem.

---

### Post by jcredberry on 2011-09-08
Solved. BIOS option was deactivated. Now I'm running my code with full 8 threads, although obviously, the benefit is far from linear.

Thanks for all your help.

---

### Post by haqking on 2011-09-08
> **jcredberry said:**
> Solved. BIOS option was deactivated. Now I'm running my code with full 8 threads, although obviously, the benefit is far from linear.

Thanks for all your help.


HA HA awesome, see my first post to you, post #2 where i asked is it enabled in bios ;-)

anyways got it sorted in the end. im glad.

remember to mark the thread as solved from thread tools.

cheers

---

### Post by pietrvanhelsing on 2013-04-24
"This allows a hyper-threading processor to appear as the usual "physical" processor and an extra "logical" processor to the host operating system (legacy operating systems see two "physical" processors)"
- this is from the Wikipedia article. It suggests that extra physical processors were made to appear on older systems (legacy).
Personal experience of Core i5 and Dual-dual Xeons with 2.6.38.8 homebrew on the one, and 12.10 on the other, suggests the same result.

Presumably one would have to be using <2.6.38 to obtain the *appearance* of extra physical cores.

Edit- further research shows that my Dual Dual Xeon may in fact only be a dual CPU-single core setup, so my seeing 4 CPU's may in fact be precisely because HT is enabled.
Of course, HT MUST be enabled in the BIOS first.

---

### Post by wildmanne39 on 2013-04-24
Thread closed. Please do not post in old threads.

---

