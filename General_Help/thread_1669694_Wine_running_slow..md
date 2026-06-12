---
title: "Wine running slow."
date: 2011-01-18
forum: General Help
---

### Post by LinuxLynx on 2011-01-18
Hello guys, I just recently used Linux (Ubuntu) about 2 weeks ago and my problem is Wine runs slow for me. I read a couple of threads and saw that many users are running Wine, maybe not exactly, like windows. I tried a couple of programs (iTunes, RA2,CS, etc..) and their all laggy. I installed the latest stable version of Wine from Winehq if I'm not mistaken.

Is it with the system?
> processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU D410   @ 1.66GHz
stepping	: 10
cpu MHz		: 1666.449
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3332.89
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU D410   @ 1.66GHz
stepping	: 10
cpu MHz		: 1666.449
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3333.31
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

[I used /proc/cpuinfo to get these information.]

or am I just doing wrong?

I haven't tried uninstalling/reinstalling it (which I do not know how) so maybe either of the two might be the problem..

BTW I just got this new pc(hardware and Ubuntu pre-intalled) two weeks ago so added infos are very much appreciated :)

Thanks! Cheers! :popcorn:

---

### Post by mastablasta on 2011-01-18
wine is using virtualizaiton of sort and that's why to run good it needs plenty RAM and more processor power. 
 
another issue might be poor graphics card driver.

---

### Post by davidmohammed on 2011-01-18
err not quite - wine just translates windows api calls to their linux equivalents - it shouldnt take anymore processing power than normal windows.  I've often found it to be faster!

I note the OP is using an Atom - not the fastest processor in the world.  Likewise I concur, maybe the graphics card.

---

### Post by LinuxLynx on 2011-01-18
Thanks for the answers, I'll be replacing my graphics card then :D

---

