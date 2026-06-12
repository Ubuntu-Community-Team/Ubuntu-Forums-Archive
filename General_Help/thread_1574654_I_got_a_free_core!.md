---
title: "I got a free core!"
date: 2010-09-14
forum: General Help
---

### Post by cyprys on 2010-09-14
Some time ago my CPU went from (correct) AMD Athlon II X3 440 to (incorrect) AMD Phenom II X4 B40 and actually dropped on computing power.

Possible reasons behind such system behaviour:
[list]
[*]*Asrock UUC* or similar BIOS feature letting you to unlock the core previously locked by a manufacturer so try to turn it off,
[*]Hyperthreading feature sometimes causing miscalculation regarding processors number, as suggested by [Claus7](http://ubuntuforums.org/member.php?u=164533) in [post=9920949]**this post**[/post], so try to turn it off or change the mode if available,
[*]weak Main-board battery, as suggested by [robert shearer](http://ubuntuforums.org/member.php?u=429439) in [post=9921068]**this post**[/post], so try the battery exchange,
[*]it wouldn't hurt to boot up into older kernel or from Live CD to see if the problem persists.
[/list]

For starters, throwing a result of *cat /proc/cpuinfo* would be a good idea.

If you have more possible reasons of such malfunction, please, write in this thread and I'll update the first post so we will save the work for newcomers.

In my case the reason was UUC. Unlocked core actually didn't have any computing power so 7200 GHz (which was used by three cores before with 2400 MHz available for each) divided by four giving the amount of 1800 GHz per core. Unfortunately, the fourth core is broken and doesn't interrupt the central bus correctly slowing it down drastically and lowering the overall possibility of using cache by other cores. As far as I've been informed such core can still be used with it's full potential providing someone writes a custom driver especially for this CPU, and this is far beyond possibilities of standard Ubuntu user and beyond the manufacturer's budget (it's simply cheaper to sell it as triplet).

Cheers,
Cyprys

---

### Post by 3Miro on 2010-09-14
To check how many cores you have, you can use:

```
 cat /proc/cpuinfo | grep cores 
```

Here is what I have:
```
  $ cat /proc/cpuinfo | grep cores
cpu cores	: 2
cpu cores	: 2

```

Alternatively, you can to System -> Admin -> System Monitor and in the Recourses tab, you can see the cores and the load for each one.

If you think the kernel messed up, you can try older kernel. Either boot from a live CD for 10.04 (not 10.04.1 which will have the latest kernel) or hold shift while booting and when the menu pops up, select an older kernel.

Another option will be to try a live CD of another distribution. Linux Mint, Fedora and Sabayon have nice LiveCDs with probably different kernel versions.

---

### Post by cyprys on 2010-09-19
No. I'm sorry I didn't make myself clear. Today I made a clean install from CD and this is what I see after upgrade to current kernel:
```

cyprys@blackshit:~$ cat /proc/cpuinfo | grep cores
cpu cores	: 4
cpu cores	: 4
cpu cores	: 4
cpu cores	: 4

cyprys@blackshit:~$ cat /proc/cpuinfo | grep -e 'model name' -e 'core id' -e MHz
model name	: AMD Phenom(tm) II X4 B40 Processor
cpu MHz		: 1800.000
core id		: 0
model name	: AMD Phenom(tm) II X4 B40 Processor
cpu MHz		: 1800.000
core id		: 1
model name	: AMD Phenom(tm) II X4 B40 Processor
cpu MHz		: 1800.000
core id		: 2
model name	: AMD Phenom(tm) II X4 B40 Processor
cpu MHz		: 1800.000
core id		: 3

```

The thing is I have **AMD Phenom X3 8750 (2400 MHz)**. I wish I checked the output before upgrade... I'll try to load older kernel tomorrow.

By the way, is it possible Asrock UUC actually unlocked the core closed by AMD? If so, how to benchmark each core or how to force an application to work on only one particular core in Ubuntu? This way I could run four threads, each on one core and see if it's truly unlocked or one is unused and only causes trouble.

Thank you for your effort.

---

### Post by cyprys on 2010-10-03
I've just installed Maverick 10.10 (with *update-manager -d*) and the problem persists. I'll try a fresh install when it comes out officially but still, **this is weird**.

---

### Post by Claus7 on 2010-10-03
Hello,

as a result you bought a triple core machine and resulted having a 4 core one! Lucky you! If I were in your shoes, I would be sooo happy!

Now, concerning your problem, one thing I could tell you is: do you know if hyperthreading is enabled in your BIOS? Sometimes, this option causes the operating system to miscalculate the number of processors, resulting in errors like those you mention.

Other than that, an old ubu cd would be nice to check, so as to eliminate the version and kernel hypothesis.

Regards!

---

### Post by sloggerkhan on 2010-10-03
I think my machine is messed up... came across this thread and got this:
```
cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Athlon(tm) X2 Dual Core Processor BE-2350
stepping    : 2
cpu MHz        : 1000.000
cache size    : 512 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips    : 2008.88
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

```

Is it just me or is only 1 core being reported? Or does the sibling mean it's really reading both?

---

### Post by 4Orbs on 2010-10-03
I've spent the past week doing some casual online research of the AMD triple core processors. If my understanding is correct, the older x3 processors (those made prior to the Phenom II series) are actually quad cores that were victims of a manufacturing defect and as a result have one of the cores disabled, thus becoming usable and sold as three core cpu. There are some motherboards with which you can enable one of the overclocking features and it will unlock the fourth core of these particular tri-core processors. It seems that when the AMD company found out about the glitch which allowed the fourth core to be unlocked, they quickly pushed the motherboard manufacturers to modify the BIOS in those boards to prevent the unlocking of the fourth core.

I suspect that if you were to update the BIOS on your motherboard, you would suddenly find yourself using a three core processor again.

---

### Post by robert shearer on 2010-10-03
Well, I have no such esoteric wondrous machine, so don't know if this will be of use.

A while back I experienced something similar when I booted up to find my previously AMD 1800+ cpu had become overnight an AMD 1500.

A lot of fiddling finally led me to believe the BIOS was not recognising the cpu correctly and as a first step I replaced the cmos battery.

That solved it instantly and for a total of $3 only. :)

Since read that it is characteristic of AMDs to under-report when the battery begins to fail. May be worth checking yours.

---

### Post by cyprys on 2010-10-04
I am stupid, so terribly stupid! I asked if it can be caused by the *Asrock UUC* feature - of course it can - it IS! I just forgot to turn it off. Damn it, so much of computing power wasted. I could easily achieved almost a thousand iterations per second more all this time by simply disabling UUC, but no, I'm the wise guy... ****!

Next time I ask stupid question, someone kick me, please.

Editing first post to spare some poor souls reading the whole thread and marking as SOLVED.

---

