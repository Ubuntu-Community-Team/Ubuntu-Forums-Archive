---
title: "Macbook 3,1 incorrect ram readings, no 64-bit, very unhappy :-("
date: 2010-10-31
forum: General Help
---

### Post by sha.goyjo on 2010-10-31
Hey all. I know that this is more of an Apple users problem, but as it's something that I've never run across before, I thought that I'd post it on the main forums and see if anybody had any idea WTF was going on.

So when I say that this is one problem, what I actually mean is that this is multiple problems. Problemma the 1st, I have put 4GB of ram into the machine, 2 pc-5300 sodimms (the machine's official max, although it can supposedly support six, in a 4,2 configuration). Any operating system booted on the machine insists that there is only 2GB of ram on the system, 1GB in each slot. That includes OSX, Windows 7 64 bit, and Ubuntu 10.10 32 bit.

The other problem (and this is the really annoying one) is that I cannot seem to boot 64 bit OS's natively. OSX refuses to boot in 64 bit mode, even with the 6 and 4 keys pressed, or config file changes made, or what have you. The 64 bit kernel simply will not go. Windows 7 64 bit will install from the CD, and as long as you boot from the CD and then skip the install prompt it will boot to the installed copy of windows. It will not boot without the CD in the drive. Ubuntu 10.10 64 bit will not boot. It sits at a prompt which says:

1.

2.

Choose CD boot method:

Ubuntu 10.10 32 bit will boot just fine.

Here are some more detailed system specs if that helps anybody.

Intel Core 2 Duo 2.00 GHZ
Intel gma x1300 graphics
4 GB pc 5300 sdram
80 GB hdd
64 bit EFI
Currently installed OSX 10.6.4, but that can change (and will as soon as I can get 64 bit ubuntu on here !)

Thanks for any help you can give.

---

### Post by cariboo on 2010-10-31
It sounds like you have a corrupted/improperly burned 64-bit CD. The first thing to do is check to see if the md5 sums match, if they don't you'll have to download and burn a new image.

To check if your hardware is detected properly boot from the 32-bit cd and once at the desktop, open a terminal and type:

```
free -m
```

to check the ram, I only have 2Gb ram, but the results looks something like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2008       1233        775          0         71        606
-/+ buffers/cache:        555       1453
Swap:         1906          0       1906
```

to check the cpu, in the same terminal type:

```
cat /proc/cpuinfo
```

I've got an Intel e5400, I'm not sure if it is a core 2 duo, but it does have two cores. The above command will probably give you more info than you need, but it will give you the right info.

```
cat /proc/cpuinfo
```

the output should look something like this:

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Pentium(R) Dual-Core  CPU      E5400  @ 2.70GHz
stepping	: 10
cpu MHz		: 1203.000
cache size	: 2048 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5399.79
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Pentium(R) Dual-Core  CPU      E5400  @ 2.70GHz
stepping	: 10
cpu MHz		: 1203.000
cache size	: 2048 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 5399.95
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

---

### Post by dcstar on 2010-11-01
> **sha.goyjo said:**
> 
..........
So when I say that this is one problem, what I actually mean is that this is multiple problems. Problemma the 1st, I have put 4GB of ram into the machine, 2 pc-5300 sodimms (the machine's official max, although it can supposedly support six, in a 4,2 configuration). Any operating system booted on the machine insists that there is only 2GB of ram on the system, 1GB in each slot. That includes OSX, Windows 7 64 bit, and Ubuntu 10.10 32 bit.
..........

Some MBs will only accept 1GB maximum chips in each slot, **make 100% sure** that your system can use larger chips.

---

### Post by kelvin spratt on 2010-11-01
Are you sure its a 64bit processor as the same command on my setup states I have a 64bit x2  possessor.

---

