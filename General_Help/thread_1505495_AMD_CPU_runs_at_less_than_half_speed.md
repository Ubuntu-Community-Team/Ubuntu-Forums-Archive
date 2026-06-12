---
title: "AMD CPU runs at less than half speed"
date: 2010-06-09
forum: General Help
---

### Post by brendand on 2010-06-09
I have a machine currently running Debian Lenny on which I would like to run Ubuntu for the driver support in its newer kernel. However, I did a test boot from the installation CD and it appears to be running at less than half its rated speed.  This is the output from the Debian kernel:

brendand@kant:~$ uname -a
Linux kant 2.6.26-2-amd64 #1 SMP Wed May 12 18:03:14 UTC 2010 x86_64 GNU/Linux
brendand@kant:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping	: 2
cpu MHz		: 2299.915
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 4603.61
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

Note that: cpu MHz	: 2299.915

This is the output from Lucid:

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips        : 1999.92
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

Note that: cpu MHz	: 1000.000

Maybe this is some sort of power save bug where the CPU speed is incorrectly scaled back.  Has anyone else encountered this problem?  Should I report it as a bug, and, if so, how do I do that?

Thanks.

Brendan

---

### Post by Breambutt on 2010-06-09
I think it only means that the AMD Cool'n'Quiet drivers work out of the box in Ubuntu. You can of course configure the level of stress it takes before the CPU starts running on higher frequencies. Cool'n'Quiet in general goes to the lowest supported frequency when you're floating on idle loads and hits the ceiling (temporarily) when opening apps and running intensive tasks (On Demand policy). This is most of the time more energy efficient than forcing powersave mode if you're going to do any kind of work since it'll get the job done faster and return to a better state sooner.

Too much information? I'm hoping some über dork is interested!

P.S. Add the CPU applet to the main bar to monitor the frequency and policies.

---

### Post by philinux on 2010-06-09
It's just the cpu scaling governor. You can add this applet to a panel. The default is usually ondemand.

Everything is ok.

---

### Post by brendand on 2010-06-09
That is what I would expect, cpu scaling down when idle and cpu scaling up on demand.  However, I first noticed this problem because my cpu intensive application ran at less than half the speed I expected, so obviously the on demand feature is not working.

I had a look at the cpu scaling applet and when I set it to 2.3 GHz, that was reflected in the cpuinfo.  That is good.  But I guess that turns off power saving when idle.

I am not quite sure what to do here.  Of course I want to save power when idle, but I want the cpu to scale up on demand, which it doesn't appear to be doing...

I plan to set this box up as a headless server running in text mode.  Is there a way to control the cpu scaling from the command line?

Brendan

---

### Post by Breambutt on 2010-06-09
Is the CnQ enabled in BIOS?

I'm controlling my headless Lenny server with cpupowerd since it also undervolts without much hassle, but you might be better off with another solution since my OEM CPU only has 2 steps and setting voltages (if you swing that way) manually for all of them might prove a bit boring. I also tried Ubuntu server before picking Debian because undervolting and manual CPU scaling seemed a little more trivial.

Linux-phc ([http://www.linux-phc.org/wiki/doku.php?id=amd_k8_processors](http://www.linux-phc.org/wiki/doku.php?id=amd_k8_processors)) is one option but if you're using it for a regular LAMP operation or nothing intensive you could just set it all from BIOS. The downside is that it would require a reboot to change this should you need more power.

All in all I have a little mixed opinions about all the options. :\

---

### Post by brendand on 2010-06-09
OK, I have done some further reading and testing and I now think Philinux is correct and that my system is actually working as expected.

Firstly, I found the package cpufrequtils.  This contains cpufreq-info and cpufreq-set, the former giving you information about the profiles and frequencies your cpu supports, the latter allowing you to set them to particular values when run as "root".  I had a play with these and satisfied myself that they were apparently working...

As an aside to this, you need some sort of power management module loaded for this to work, lsmod to check, modprobe to load.  On my system, it is powernow-k8.  And, of course, you may have a BIOS setting you may have to enable, such as 'cool and quiet' in my BIOS.

As for my "benchmarking", well that produced results which had me confused at times, but in the end, the inconsistencies seemed to indicate a problem with my program, NOT the frequency scaling, since I got inconsistent results from one run to the next under the same frequency scaling conditions.  I have some ideas why that may be, and I will try and fix them and do some more testing for my own personal satisfaction.

For the time being though, I think my "problem" was simply my ignorance and thanks to your replies, I am now a little less ignorant... :-)

Thanks.

Brendan

---

### Post by dcstar on 2010-06-10
> **brendand said:**
> That is what I would expect, cpu scaling down when idle and cpu scaling up on demand.  However, I first noticed this problem because my cpu intensive application ran at less than half the speed I expected, so obviously the on demand feature is not working.

I had a look at the cpu scaling applet and when I set it to 2.3 GHz, that was reflected in the cpuinfo.  That is good.  But I guess that turns off power saving when idle.

I am not quite sure what to do here.  Of course I want to save power when idle, but I want the cpu to scale up on demand, which it doesn't appear to be doing...


Install the powernowd package and configure it how you like.

You can set things so "niced" apps do not trigger CPU ramping, I have my BOINC apps running  and keeping my CPUs at 100% but they do not ramp up my CPU clock rate - only other apps can trigger that.

---

### Post by asrman on 2011-12-12
# I also have this problem. Is anybody can suggest me how to handle it? Thanks

cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 9
model name      : AMD Opteron(tm) Processor 6168
stepping        : 1
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 12
core id         : 0
cpu cores       : 12
apicid          : 16
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid amd_dcm pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips        : 3800.11
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

.....


processor       : 46
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 9
model name      : AMD Opteron(tm) Processor 6168
stepping        : 1
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 3
siblings        : 12
core id         : 4
cpu cores       : 12
apicid          : 74
initial apicid  : 58
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid amd_dcm pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips        : 3800.12
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
 
processor       : 47
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 9
model name      : AMD Opteron(tm) Processor 6168
stepping        : 1
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 3
siblings        : 12
core id         : 5
cpu cores       : 12
apicid          : 75
initial apicid  : 59
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid amd_dcm pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips        : 3800.12
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

---

### Post by oldtimer7777 on 2011-12-12
It is normal. Go back a few replies to see what they wrote.

> **asrman said:**
> # I also have this problem. Is anybody can suggest me how to handle it? Thanks

cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 9
model name      : AMD Opteron(tm) Processor 6168
stepping        : 1
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 12
core id         : 0
cpu cores       : 12
apicid          : 16
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid amd_dcm pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips        : 3800.11
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

.....


processor       : 46
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 9
model name      : AMD Opteron(tm) Processor 6168
stepping        : 1
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 3
siblings        : 12
core id         : 4
cpu cores       : 12
apicid          : 74
initial apicid  : 58
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid amd_dcm pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips        : 3800.12
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
 
processor       : 47
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 9
model name      : AMD Opteron(tm) Processor 6168
stepping        : 1
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 3
siblings        : 12
core id         : 5
cpu cores       : 12
apicid          : 75
initial apicid  : 59
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid amd_dcm pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips        : 3800.12
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

---

