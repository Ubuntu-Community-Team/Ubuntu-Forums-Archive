---
title: "Ubuntu 10.10 amd64 and VirtualBox amd64"
date: 2010-10-22
forum: General Help
---

### Post by phacer on 2010-10-22
Hi,

I'm a new emigrant to the lovely Ubuntu world. But I can't fully emigrate since I need some windows apps. So I thought I should install VirtualBox on my ubuntu to run windows and what I need.

After intstalling Ubuntu 10.10 amd64 all the updates and the latest 64 bit version the graphics driver I install VirtualBox amd64. 
I create a VM for windows and set it up to use 5GB of ram. Then I run it and before the VirtualBox and Oracle logo comes up it crashes and says VT-x not available (VERR_VMX_NO_VMX). 
It works if I use less ram but that would be useless for me and all the graphic programs I use at the same time. 
I have tried what I read on another thread about changing some stuff in one of the xml files about VT-x but no luck.

Has this happened to anyone else and does anyone have any suggestions of what to do?

My specs are:
Intel Pentium Dual Core 2.6 GHz
Asus P5Q SE motherboard
8 GB Ram
Nvidia 9600 GT

---

### Post by sanderd17 on 2010-10-22
There is no point in giving 5 GB ram to a 32-bit OS (the virtual windows), a 32-bit OS can only access up to 3.5 GB ram.

So if it works with less ram, do it that way.

---

### Post by phacer on 2010-10-22
So I can't install a 64 bit version of Windows then?

---

### Post by Quackers on 2010-10-22
I don't know whether I had the same problem exactly (because I can't remember) but I could not install a 64 bit OS in VB. It would only allow me to install a 32 bit OS, even though my host system is 64 bit Ubuntu.

---

### Post by phacer on 2010-10-22
Strange that virtualbox has a 64 bit version then.

---

### Post by plucky on 2010-10-22
> **Quackers said:**
> I don't know whether I had the same problem exactly (because I can't remember) but I could not install a 64 bit OS in VB. It would only allow me to install a 32 bit OS, even though my host system is 64 bit Ubuntu.

I have 10.10_AMD64 guest running in 10.04_AMD64 Host.


> Then I run it and before the VirtualBox and Oracle logo comes up it crashes and says VT-x not available (VERR_VMX_NO_VMX). 

This could be the problem with Intel Processors as it has to have the VMX Flag set for the CPU.

If you open a terminal and ```
cat /proc/cpuinfo
``` and look for the VMX flag under the CPU Flags.If it isn't there,you won't be able to run a 64-bit guest.

You might also get a more informed response in the [Virtualisation Forum](http://ubuntuforums.org/forumdisplay.php?f=308) where the experts hangout.

Good Luck

---

### Post by Quackers on 2010-10-22
I do have the vmx entry in the flags section

flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida dts tpr_shadow vnmi flexpriority

but I seem to remember thinking at the time that it may have been a hardware or bios problem. I'm sure vmx was mentioned in the error I got.

---

### Post by phacer on 2010-10-22
I don't have a vmx flag, so it might be time for a new CPU. Thanks for you reply.

---

### Post by AgenT on 2010-10-22
Something is wrong. VirtualBox should not crash even if your CPU does not have VT-X and VirtualBox option for vt-x is checked.

Make sure you do not have any other VM installed, such as xen or kvm. In the VirtualBox manual it states that if you have kvm installed, it will crash VirtualBox. Two VMs cannot function together because they cannot know what the other one is doing.

If you do not have vmx entry in when doing cat /proc/cpuinfo then look in your BIOS. It may be disabled. Look for a CPU entry and a "Virtualization" and "VT-X" option. If not, you don't have it.

64-bit VirtualBox works perfectly on my Ubuntu 10.10 64-bit host with VT-X enabled. It's very fast, too.

---

### Post by Darth Penguin on 2010-10-22
You need 64 bit Windows to use more than 3.5 GB of RAM.

---

