---
title: "VirtualBox VERR_VMX_NO_VMX"
date: 2012-09-17
forum: General Help
---

### Post by Kirk Schnable on 2012-09-17
I have used my desktop at work for a year with Oracle's VirtualBox product to manage several VMs.  

After wiping my machine and upgrading from 10.04 to 12.04, I am now having this error when attempting to start a virtual machine:
VERR_VMX_NO_VMX

I understand from my reading that this is supposed to be a BIOS setting, but I have looked through them and I have not seen anything to this effect.  It also doesn't make sense to me that this would become a problem after a software upgrade, if it is a BIOS setting causing this problem.

I have tried several suggestions I've found on Google, such as changing the VirtualBox machine file to not need VT-x support, and using the VBoxManage command to manipulate the VM.  So far, I have not gotten any VMs to start up.

I am running kernel 3.2.0-30-generic.
I have tried VirtualBox's latest deb from the website, as well as virtualbox-ose from apt.

Here is my /proc/cpuinfo
(I am reading that VT-x needs a CPU flag, from this BIOS setting... so this may be useful?)
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
stepping	: 10
microcode	: 0xa0b
cpu MHz		: 2800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm
bogomips	: 5599.96
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
stepping	: 10
microcode	: 0xa0b
cpu MHz		: 2800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm
bogomips	: 5599.82
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

Any input the community might have for me would be appreciated!

Thanks,
Kirk

---

