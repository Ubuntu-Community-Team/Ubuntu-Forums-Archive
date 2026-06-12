---
title: "Can't run with more then one processor enabled"
date: 2011-03-13
forum: General Help
---

### Post by coweatyou on 2011-03-13
I just installed ubuntu and while I was able to run with all 8 processors at first.  After a few restarts it started to hang on the line:
```
Booting Node   0 Processors #1
```The only way to always advance past that point is to disable all but one processor in the bios.  When 2 core's are enabled (HT off) I can get it to boot about 10% of the time.  Running 64 bit Ubuntu on a Core i7 910 with 6GB of RAM.

Also, once when I had all 8 processors going it actually hung at ```
Booting Node   0 Processors #1 #2 #3 #4 #5 #6
```I haven't been able to tell what was different that time.

EDIT: I should also probably mention that I had to take quiet out of the boot options in grub to get it to run at all (otherwise I only get a blank screen with a flashing cursor).  I don't know if these problems are related.

---

### Post by |{urse on 2011-03-13
please post the output of 

> cat /proc/cpu

---

### Post by coweatyou on 2011-03-13
> **|{urse said:**
> please post the output of

```
pat@pat-desktop:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
stepping	: 4
cpu MHz		: 1596.000
cache size	: 8192 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc up arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5333.50
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

This is with only one processor enabled.

EDIT: Just got it to start up with 2 processors:
```
pat@pat-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
stepping	: 4
cpu MHz		: 2661.000
cache size	: 8192 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5334.07
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
stepping	: 4
cpu MHz		: 2661.000
cache size	: 8192 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 5333.55
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

---

### Post by coweatyou on 2011-03-13
Ok, did some more testing and it looks to be a strange hyperthreading problem.  If I run without hyperthreading enabled everything boots fine.  Also if I run with only one core and hyperthreading enabled it still works.  As soon as I turn on more then one core with hyperthreading on it stops working.

Even more strange is if I run with more then one core and hyperthreading I will still get the problem even if I disable hyperthreading.  The only way to fix the problem is to go back to 1 processor without hyperthreading and it seems to clear the problem.

---

### Post by cbowman57 on 2011-03-13
Try adding acpi=ht to your grub kernel command line and see if that makes a difference.

[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

Could be it's just a detection problem.

---

### Post by coweatyou on 2011-03-13
> **cbowman57 said:**
> Try adding acpi=ht to your grub kernel command line and see if that makes a difference.

[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

Could be it's just a detection problem.

Still didn't work, but at least I was just able to just restart without HT and didn't have to disable 3 core's again.

---

### Post by cbowman57 on 2011-03-13
Have you checked the manufacture website to see if there might be a bios upgrade for your motherboard?

I've only got 2 cores so I'm just thinking out loud in the hopes that we'll stumble upon a solution.

---

### Post by cbowman57 on 2011-03-13
What happens is you use maxcpus=8?[http://oreilly.com/linux/excerpts/9780596100797/kernel-boot-command-line-parameter-reference.html]("http://oreilly.com/linux/excerpts/9780596100797/kernel-boot-command-line-parameter-reference.html")

---

### Post by coweatyou on 2011-03-13
> **cbowman57 said:**
> Have you checked the manufacture website to see if there might be a bios upgrade for your motherboard?

I've only got 2 cores so I'm just thinking out loud in the hopes that we'll stumble upon a solution.

That did it.  For future searchers, I have an intel DX58SO motherboard and updating from the Sept 08 drivers to the Dec 10 drivers fixed it (at least for 2 boots so far.  Also, it was not a HT problem after all as an attempt to reboot with 4 cores and no HT stalled booting processor 3.

---

### Post by cbowman57 on 2011-03-13
> **coweatyou said:**
> That did it.  For future searchers, I have an intel DX58SO motherboard and updating from the Sept 08 drivers to the Dec 10 drivers fixed it (at least for 2 boots so far.  Also, it was not a HT problem after all as an attempt to reboot with 4 cores and no HT stalled booting processor 3.
So, you're now running all 8 cores hyperthreaded after a bios update?

I bet she's running like a new machine now. ;-)

---

### Post by coweatyou on 2011-03-13
> **cbowman57 said:**
> So, you're now running all 8 cores hyperthreaded after a bios update?

I bet she's running like a new machine now. ;-)

Well she was fast before in windows, but I needed linux to compile a program using a library that wasn't in cygwin that I couldn't get to work.  Being back on linux on a powerful computer (my other linux install is on a 6 year old laptop) reminds me just how great it is.  Linux actually loads faster then the bios does.

---

### Post by |{urse on 2011-03-14
Just checked back in on this thread. Glad everything is working correctly now. ^^

---

### Post by wildmanne39 on 2012-08-12
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

