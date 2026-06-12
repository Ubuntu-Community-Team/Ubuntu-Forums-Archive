---
title: "Enable SMP &quot;symmetric multiprocessing&quot; Support in Ubuntu 10.04 64 bit desktop"
date: 2010-07-07
forum: General Help
---

### Post by rkumar110001 on 2010-07-07
I installed ubuntu 10.04 64 bit on Inspiron 1525. I also installed virtualbox to have a windows instance just in case.
Everything works fine but I can not assign 2 cpu's to the machine. Ubuntu shows only 1 processor.I googled and found there is something called SMP has to be enabled. I don't know how to do it, please help. Is it for sure kernel issue or do I need to make changes to VirtualBox.

**grep SMP /boot/config-`uname --kernel-release` output >>**
CONFIG_USE_GENERIC_SMP_HELPERS=y
CONFIG_X86_64_SMP=y
CONFIG_SMP=y
# CONFIG_X86_VSMP is not set
# CONFIG_MAXSMP is not set
CONFIG_PM_SLEEP_SMP=y
CONFIG_SCSI_SAS_HOST_SMP=y
CONFIG_VIDEO_VP27SMPX=m

**uname -a output >>**
Linux computer 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

**cat /proc/cpuinfo output**
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3989.43
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3989.99
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

