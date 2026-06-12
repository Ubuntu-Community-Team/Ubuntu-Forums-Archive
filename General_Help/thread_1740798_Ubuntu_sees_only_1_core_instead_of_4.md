---
title: "Ubuntu sees only 1 core instead of 4"
date: 2011-04-27
forum: General Help
---

### Post by fw12 on 2011-04-27
I hope somebody can help me.

Why does ubuntu only see a single core on my quad-core cpu?
All cores are enabled in the bios.

Here are some details about my hardware...


$ dmesg | grep Phenom
[    0.812775] powernow-k8: Found 1 AMD Phenom(tm) II X4 810 Processor processors (1 cpu cores) (version 2.20.00)


$ uname -a
Linux xyz 2.6.32-31-generic-pae #61-Ubuntu SMP Fri Apr 8 20:00:13 UTC 2011 i686 GNU/Linux


$ cat /proc/cpuinfo | grep processor | wc -l
1


$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid


$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 810 Processor
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
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
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc up nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5222.30
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

---

### Post by TeoBigusGeekus on 2011-04-27
Perhaps you should install the 64bit version.

---

### Post by fw12 on 2011-04-27
Thx for your reply.

I doubt 32-bit is the problem.  I have an i386 CentOS machine that shows all the cores, as shown below...


$ uname -a
Linux xyz 2.6.18-194.32.1.el5PAE #1 SMP Wed Jan 5 18:43:13 EST 2011 i686 athlon i386 GNU/Linux


$ cat /proc/cpuinfo | grep processor | wc -l
2


$ cat /etc/redhat-release 
CentOS release 5.5 (Final)

---

### Post by falko on 2011-04-27
You need an SMP kernel.

---

### Post by lithopsian on 2011-04-27
This kernel claims to be SMP.  Ubuntu kernels are SMP unless you go and get a weird one or build it yourself.  Check dmesg and see if it says anything about the cores.

---

### Post by fw12 on 2011-04-27
The kernel I have says SMP.  Here is output from dmesg

$ dmesg | grep SMP
[    0.000000] Linux version 2.6.32-31-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #61-Ubuntu SMP Fri Apr 8 20:00:13 UTC 2011 (Ubuntu 2.6.32-31.61-generic-pae 2.6.32.32+drm33.14)
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.020467] SMP alternatives: switching to UP code
[    0.025272] Freeing SMP alternatives: 20k freed
[    0.048056] SMP motherboard not detected.
[    0.052001] SMP disabled



The last two lines says:

[    0.048056] SMP motherboard not detected.
[    0.052001] SMP disabled

Is that where the problem lies, that is preventing more than one cpu core to be seen?

SMP seems to be associated with multiple cpu's, not multi-core cpu.

---

### Post by lithopsian on 2011-04-27
Could be a BIOS issue.  Have a shuffle through the BIOS menus and see if you can find anything related to this.  There might also be confusion with your APIC or ACPI settings.  Maybe there are more clues in the dmesg output.

---

### Post by lithopsian on 2011-04-27
> **fw12 said:**
> 

SMP seems to be associated with multiple cpu's, not multi-core cpu.

Linux treats the cores as separate CPUs.  Or should!

---

### Post by fw12 on 2011-04-28
You guys are very helpful with your comments and suggestions.

I'll look closer at the bios, as well as apic/acpi.

I'll post later what I find.

---

### Post by fw12 on 2011-04-28
Here's what I did...

# vim /etc/default/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic acpi=off"

# update-grub2 

# reboot

$ cat /proc/cpuinfo | grep processor | wc -l
4

My Asus M4a785T-M/CSM mobo clearly has issues with APIC.

Thanks to everybody, particularly lithopsian for mentioning APIC.

---

