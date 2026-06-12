---
title: "Ubuntu won't boot when Virtualization Technology is enabled in my BIOS"
date: 2012-01-21
forum: General Help
---

### Post by leth on 2012-01-21
If I enable "Virtualization Technology" in my BIOS, Ubuntu will no longer boot.  It boots past grub, but the screen is blank (with the purple shading at the bottom) and the computer is frozen (Caps Lock and Num Lock do not respond.)  FWIW, Windows 7 boots just fine.  And Ubuntu works just fine with virtualization disabled.

This is in an HP tm2 laptop with the most up-to-date BIOS version.  The CPU is an Intel U7300 @ 1.3GHz.  I am running Ubuntu 11.10 32-bit with all the latest updates.

Any hints on how to troubleshoot this?  I tried removing "quiet splash" from the startup commands in grub but that just gives me a blank screen with a flashing cursor and the computer still locks up.  So it seems like it's something in the kernel.

Here's some info from /proc/cpuinfo:

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Genuine Intel(R) CPU           U7300  @ 1.30GHz
stepping    : 10
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips    : 2593.68
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor 1 shows the same info as above.

---

### Post by xyzzyman on 2012-01-21
Are you running just a kernel from repository? Or have you put a 3.2 kernel in?

Also can you boot from a live cd/usb?

---

### Post by leth on 2012-01-21
I am using 3.0.0-15-generic-pae from the repository (uname -a shows: Linux tm2 3.0.0-15-generic-pae #25-Ubuntu SMP Mon Jan 2 19:40:15 UTC 2012 i686 i686 i386 GNU/Linux)

I'll give the live CD a try tomorrow night (don't have it with me at the moment)

---

### Post by imachavel on 2012-01-21
Intel U7300 @ 1.3GHz? Maybe the processor doesn't have enough memory to run virtual code. If it does, then it could just be ubuntu doesn't support virtual code for your version of the bios. Then you said it's the latest version.

here is my uname -a:

3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:45:26 UTC 2012 i686 i686 i386 GNU/Linux

well I don't know. that processor is very under clocked, I don't know much about it's architecture or much about over clocking in Linux. Ummmmmmmmmmmmmmmmmmmm, what do you need the virtual support in the bios for? Are you trying to run hard drive encryption with v pro? Virtual code is written in Java correct? Whatever the task is, it seems you would rather use linux with virtual support then windows 7.

Am I getting warmer?:

[http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/](http://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/)

---

### Post by imachavel on 2012-01-21
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping    : 1
cpu MHz        : 2793.068
cache size    : 1024 KB
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
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 5586.13
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping    : 1
cpu MHz        : 2793.068
cache size    : 1024 KB
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
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 5585.98
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:


I've got 32 bits virtual, you've got 48 bits virtual. a 48 bit processing virtual bus on the mobo? and enabled in the bios? But ubuntu won't boot like that? Crazy. Just nuts, do you need virtual support for some kvm networking task you need to perform that needs virtual bios support? Doesn't sound right. Ubuntu is usually more well known for supporting this type of stuff then anything else, maybe there is an ubuntu repository or home system folder bit of code that hasn't been updated that is keeping ubuntu from wanting to boot with the virtual bios support enabled before ubuntu boots in hdd drive or whatever you are booting it from.

Have you tried sudo apt-get install update? Then rebooting with the virtual bios support enabled? Maybe you need to install something from terminal after downloading it and trying again. Good luck please post if you fix it or not.

---

### Post by xyzzyman on 2012-01-21
He's already done all the latest updates. Also his address sizes are correct. My Core2 Duo has

```


processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
stepping	: 6
microcode	: 0x60f
cpu MHz		: 800.000
cache size	: 6144 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 5055.01
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

And I have VT enabled as I run VM's. He has just 1.3Ghz cores but speedstep has it just running at 800mhz at the moment as it should.

I would verify that it still boots from the LiveCD/USB, but until then try a non PAE kernel to rule that out. With it only being a 1.3ghz, how much ram do you have in that system?

---

### Post by leth on 2012-01-21
I've been trying to enable VT to see if it would speed things up with my Windows XP guest in VMware Player (also going to give VirtualBox a try.)  But the XP guest is working just fine.

Since my /proc/cpuinfo is showing "vmx" under the flags, does that mean virtualization is enabled or just that it's supported (but not necessarily enabled?)

I wouldn't be surprised if this was a bug in HP's BIOS might.  It took me a couple weeks to figure out that I needed to update the BIOS before ACPI started working in Ubuntu.  I'll be surprised if they release any more BIOS updates for this model so I might just have to keep using it with VT disabled.  Maybe VT won't actually give me much of an advantage anyways?  I'm not trying to do anything crazy with virtualization, just trying to run Windows for a couple must-have scenarios (e.g. can't get my Harmony remote to update using congruity)

---

### Post by leth on 2012-01-21
Also, yes, Ubuntu is fully up to date with patches.

I have 4GB RAM.

I'll be sure to give the live CD a try and let you know how it goes.

---

### Post by leth on 2012-01-21
I just tried the non-PAE kernel but it still freezes.

---

### Post by xyzzyman on 2012-01-21
> **leth said:**
> I've been trying to enable VT to see if it would speed things up with my Windows XP guest in VMware Player (also going to give VirtualBox a try.)  But the XP guest is working just fine.

Since my /proc/cpuinfo is showing "vmx" under the flags, does that mean virtualization is enabled or just that it's supported (but not necessarily enabled?)

I wouldn't be surprised if this was a bug in HP's BIOS might.  It took me a couple weeks to figure out that I needed to update the BIOS before ACPI started working in Ubuntu.  I'll be surprised if they release any more BIOS updates for this model so I might just have to keep using it with VT disabled.  Maybe VT won't actually give me much of an advantage anyways?  I'm not trying to do anything crazy with virtualization, just trying to run Windows for a couple must-have scenarios (e.g. can't get my Harmony remote to update using congruity)

In VirtualBox, don't enable IOAPIC on Windows XP systems. Runs MUCH slower. Learned that from the virtualbox support forums.

Does recovery mode boot when VT is enabled?

Do you still have a non-PAE kernel installed under 'previous versions' of grub? My gut is telling me that it's PAE and the enabling of VT but it's just a gut from past experience. EDIT: Ignore this previous part. We posted same time. At this point you can just try to see if the live CD will boot with VT enabled.

---

### Post by leth on 2012-01-23
I tried booting from the 11.10 CD with VT enabled, but it still locks up when trying to boot the kernel.  All I see is the "ISOLINUX .." screen, then the pre-boot screen (where you can press a key to setup addi I get the screen with the flashing cursor where the tional boot options), then I get the screen with the flashing cursor and the computer is frozen.

I'm wondering how far I should go with trying to troubleshoot this.  Does enabling VT really give much of a performance boost?

---

### Post by xyzzyman on 2012-01-23
> **leth said:**
> I tried booting from the 11.10 CD with VT enabled, but it still locks up when trying to boot the kernel.  All I see is the "ISOLINUX .." screen, then the pre-boot screen (where you can press a key to setup addi I get the screen with the flashing cursor where the tional boot options), then I get the screen with the flashing cursor and the computer is frozen.

I'm wondering how far I should go with trying to troubleshoot this.  Does enabling VT really give much of a performance boost?

Sometime VT runs slower for VM's. I didn't believe it at first until I started seeing some benchmarks. One my system VT is much smoother.

---

