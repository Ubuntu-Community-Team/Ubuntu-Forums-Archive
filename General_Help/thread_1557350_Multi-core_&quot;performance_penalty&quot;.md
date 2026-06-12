---
title: "Multi-core &quot;performance penalty&quot; ?"
date: 2010-08-20
forum: General Help
---

### Post by rybu on 2010-08-20
Hello, 

I've been doing some computations at home and at work and have noticed some unexpected performance issues.   The work machine is quite a bit more "serious" than the home machine, but sometimes the home machine outperforms the work machine.  I'm curious what the dynamic is -- why this should be. 

Ultimately on both machines the computations are just a lot of very large arbitrary-precision integer linear algebra computations  (based on the GNU multi-precision library). Reducing a lot of sparse but "large" integer matrices, finding the vertices on the boundary of high-dimensional polyhedra, and so on. 


On my home computer (which has two cores), if I run a standard computation on only one core (the 2nd core near-idle), it takes 282s. 

On the home computer running two identical parallel computations (the same computation as above), it takes approx 320s on each core. 

On my office computer, with all cores essentially idle except for one core running this computation, it takes 196s. 

On my office computer, if I have all 8 cores running full-out, and one of the cores is doing the computation above, it takes 356s on the one core that's running the computation.

Here are the details on my home computer:

```
 cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
stepping	: 10
cpu MHz		: 800.000
cache size	: 4096 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 4787.65
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
stepping	: 10
cpu MHz		: 800.000
cache size	: 4096 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 4787.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

rybu@rybu-laptop:~/prog/regina/exercise/4M-census/rank1/t$ 

```

and my office computer:

```

cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
stepping	: 5
cpu MHz		: 1600.000
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6147.45
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
stepping	: 5
cpu MHz		: 1600.000
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 1
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6147.36
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
stepping	: 5
cpu MHz		: 1600.000
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 2
cpu cores	: 4
apicid		: 4
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6147.19
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
stepping	: 5
cpu MHz		: 1600.000
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 3
cpu cores	: 4
apicid		: 6
initial apicid	: 6
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6147.19
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 4
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
stepping	: 5
cpu MHz		: 1600.000
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 0
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6147.31
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 5
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
stepping	: 5
cpu MHz		: 1600.000
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 1
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6147.02
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 6
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
stepping	: 5
cpu MHz		: 1600.000
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 2
cpu cores	: 4
apicid		: 5
initial apicid	: 5
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6147.17
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 7
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
stepping	: 5
cpu MHz		: 1600.000
cache size	: 8192 KB
physical id	: 0
siblings	: 8
core id		: 3
cpu cores	: 4
apicid		: 7
initial apicid	: 7
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6147.18
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

rybu@rybu-desktop:~/prog/regina/exercise/4M-census/rank1/H$ 

```

My guess is that there probably would be little to no multi-core performance penalty *if* these computations were small enough to sit in the cache ram of an individual core.  But since they're sufficiently-large, there must be a log-jam with one thread waiting for the other to finish accessing system RAM. Is it likely something like that? 

That would explain what's going on.  Is that roughly what you think is happening?  Any insights are welcome.

Also, if that is what's happening is there a way to re-code my application to somehow avoid this problem, is there a way to circumvent the log-jam of requests for system RAM?  Is there a way to parallelize that somehow, is there really only one pipeline to the system RAM?

---

### Post by hal8000 on 2010-08-20
Can you provide a bash or other script so others can provide you with some results?
Does your code take advantage of 32 bit or 64 bit instructions for multi core processors ?

You can also renice the task to give it a higher priority, this may speed up
your calculations.

---

### Post by rybu on 2010-08-20
> **hal8000 said:**
> Can you provide a bash or other script so others can provide you with some results?
Does your code take advantage of 32 bit or 64 bit instructions for multi core processors ?

You can also renice the task to give it a higher priority, this may speed up
your calculations.

Unfortunately the code I'm using is pretty specific. To duplicate what I'm doing you'd have to install the source from the Subversion repository for this software: 

[http://regina.sourceforge.net/](http://regina.sourceforge.net/)

then compile on your end, and then I'd have to give you a big data file and some additional code to allow you to process the data file....  

In short this code is fully optimized for a 64-bit environment.  Computations can occasionally get memory-intensive -- a single task can frequently have over 100Mb of RAM allocated, sometimes as much as 1Gb, but usually more in the 10Mb range. The executable is roughly 1.2Mb, and it calls upon a shared object file that's 44Mb in size -- I'm not sure how much of the code in this .so file is in active memory at any time, but at times probably a pretty decent chunk. 

I'm wondering if there are any utilities for Linux that allow many-processor machines to structure their memory in ways that allow for more efficient usage of RAM when many processors are active?  On systems with 20-80 processors usually there is a scheduler that "locks" a task into an environment with a fixed amount of RAM (and sometimes you can request memory environments for each task).  Before I thought that was a physical limitation of the computer but now I'm hopeful something like this might allow for more efficient computations?  

I'm talking about multi-processor queue managers, like Gridengine: 

[http://gridengine.sunsource.net/](http://gridengine.sunsource.net/)

Does that do what I'm asking about?

edit: okay, I figured out Gridengine isn't going to help me.  It seems like the main thing I need to do to keep performance up is to lower the memory-profile of my tasks so that it doesn't have to leave the cache as often.

---

### Post by rybu on 2010-08-23
I recently upgraded my office computer from its 4Gb RAM (on 2 memory cards) to 24Gb RAM on 6 memory cards.  

It seems the office computer has a little less of this multi-core "performance penalty" as I'm calling it. 

Is it possible for separate processes to access system RAM simultaneously if the memory processor 1 needs is on memory chip 1, and the memory processor 2 needs is on memory chip 2?   If so that would explain what's going on.  I'll try to do some benchmarking soon to compare before and after.

---

