---
title: "Kernel kobject error message"
date: 2011-07-10
forum: General Help
---

### Post by towheedm on 2011-07-10
Could someone please tell me what this kernel message means:

 ```
kobject: 'machinecheck1' (ef101ec8): does not have a release() function, it is broken and must be fixed.
```I have tried several searches on Google but could not find any meaningful answers.

These are the additional messages related to ef101ec8:

```
Jul 10 01:23:05 GA1A4CH kernel: [  370.206381] kobject: 'machinecheck1' (ef101ec8): kobject_cleanup
Jul 10 01:23:05 GA1A4CH kernel: [  370.206384] kobject: 'machinecheck1' (ef101ec8): does not have a release() function, it is broken and must be fixed.
Jul 10 01:23:05 GA1A4CH kernel: [  370.206387] kobject: 'machinecheck1' (ef101ec8): auto cleanup 'remove' event
Jul 10 01:23:05 GA1A4CH kernel: [  370.206390] kobject: 'machinecheck1' (ef101ec8): kobject_uevent_env
Jul 10 01:23:05 GA1A4CH kernel: [  370.206411] kobject: 'machinecheck1' (ef101ec8): fill_kobj_path: path = '/devices/system/machinecheck/machinecheck1'
Jul 10 01:23:05 GA1A4CH kernel: [  370.206444] kobject: 'machinecheck1' (ef101ec8): auto cleanup kobject_del
```The problem occurs after waking from hibernation.  Upon waking CPU1 does not start.  Everything works, but only CPU0 runs.  This is info from /proc/cpuinfo:

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping    : 9
cpu MHz        : 2792.797
cache size    : 512 KB
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
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5585.59
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping    : 9
cpu MHz        : 2792.797
cache size    : 512 KB
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
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips    : 5584.83
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

```Any help is greatly appreciated.

Thanks.

---

