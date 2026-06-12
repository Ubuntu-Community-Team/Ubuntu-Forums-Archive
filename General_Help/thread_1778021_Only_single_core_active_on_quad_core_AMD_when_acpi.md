---
title: "Only single core active on quad core AMD when acpi is active."
date: 2011-06-08
forum: General Help
---

### Post by bitminer on 2011-06-08
Only Single core active on quad core AMD when acpi is active.

with acpi=off
uname -a

Linux dvip4 2.6.32-30-server #59-Ubuntu SMP Tue Mar 1 22:46:09 UTC 2011 x86_64 GNU/Linux

```

cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2600.338
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb  rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid  pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm  sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5200.66
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2600.338
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb  rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid  pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm  sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5200.33
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2600.338
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 2
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb  rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid  pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm  sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5200.22
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2600.338
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 3
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb  rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid  pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm  sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5200.21
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

bdavis5@dvip4:~$ uname
Linux
bdavis5@dvip4:~$ uname -a
Linux dvip4 2.6.32-30-server #59-Ubuntu SMP Tue Mar 1 22:46:09 UTC 2011 x86_64 GNU/Linux
bdavis5@dvip4:~$ ^C
bdavis5@dvip4:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2600.338
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb  rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid  pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm  sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5200.66
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2600.338
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb  rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid  pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm  sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5200.33
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 2
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2600.338
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 2
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb  rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid  pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm  sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5200.22
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 3
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 2600.338
cache size    : 512 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 3
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb  rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid  pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm  sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5200.21
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate


```when using default settings (acpi on with acpi active in bios) only a single core is shown. 

I get 4 cores, but mouse movement and keyboard leaves something to be desired.

Previous  versions of the kernel worked and I could see 4 cores, but I am no  longer able to run 2.6.27 and 2.6.28 seems to have same issue.  going to  try 2.8.24 and see if Ubuntu update process allows me go back.


keywords: quad core, acpi, smp, multi-core, ubuntu

---

### Post by bitminer on 2011-06-08
Ok weird ... on third boot on latest kernel the 4 cores appear.  The mother board is a Foxcon Destroyer with 4 Tesla GPUs installed and I also noticed some wierd gpu enumeration issues.  I will chalk this one up to flakey hardware timing.

---

