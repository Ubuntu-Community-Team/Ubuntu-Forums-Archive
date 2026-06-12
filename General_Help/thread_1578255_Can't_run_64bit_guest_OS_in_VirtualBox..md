---
title: "Can't run 64bit guest OS in VirtualBox."
date: 2010-09-20
forum: General Help
---

### Post by darthpenguin on 2010-09-20
Hi all. I have a strange problem that I will try to explain clearly. I hope someone out there has an answer.

I have a desktop that runs 2 host OSs. Ubuntu 10.04 32bit on one partition and Windows 7 32bit on the other. In Windows I can install a 64bit guest OS in virtualbox with no problem. However, in Ubuntu I cannot install a 64bit guest OS. I get this error:

VT-x/AMD-V hardware acceleration has been enabled, but is not operational.  Your 64-bit guest will fail to detect a 64-bit CPU and will not be able to boot.

Please ensure that you have enabled VT-x/AMD-V properly in the BIOS of your host computer.

I have checked the BIOS and see no options relating to visualization. But I know the BIOS is fine because everything works in Windows. To make matters worse this isn't really an Ubuntu problem as I can install 64bit guest OSs on my MacBook Pro which is running Ubuntu 10.04 32bit as the host OS.

So why do I have this problem only on Ubuntu on my desktop? how can I fix it? Would it make a difference if the host OS was 64bit?

here is the output of egrep '(vmx|svm)' --color=always /proc/cpuinfo on my desktop

flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt

By my understanding if "svm" shows in this output everything should work.

any help would be appreciated.

Thank You.

---

### Post by SlugSlug on 2010-09-20
maybe your CPU does not support VT, I hit that prob trying to run 64bit guests

---

### Post by darthpenguin on 2010-09-20
Hey man. Thanks for the quick reply. That was my first thought too. However, Windows (which is running on the same processor - different partition) runs 64bit guest OSs just fine. So I assume the processor supports VT. Or is it because Windows has software emulation or something? I have an AMD Athlon(tm) II X4 620 Processor how can I tell if that processor actually supports VT?

Thanks

---

### Post by SlugSlug on 2010-09-20
not sure with AMD -- I know intel has whats called Virtualisation Technology

This AMD page says something about AMD Virtualization

[http://www.overclockersclub.com/reviews/athlon2_620/2.htm](http://www.overclockersclub.com/reviews/athlon2_620/2.htm)

---

### Post by darthpenguin on 2010-09-20
Yes, I see. Also AMD's official site list visualization as a feature of this processor...

[http://products.amd.com/en-na/DesktopCPUDetail.aspx?id=597]("http://products.amd.com/en-na/DesktopCPUDetail.aspx?id=597")

yet when I run the amdvhyperv.exe (in windows of course) downloaded from AMD, it says, "This utility detected that AMD Visualization (AMD-V) Technology is* not* enabled in BIOS. Enable AMD-V in Bios. Re-run this utility to further verify your system is compatible with Hyper-V."

So if visualization is supported but disabled and there is no option to enable in in the BIOS then I would assume the problem lies with the MB. But this does not answer why everything works on Windows. If AMD-V is not enabled VirtualBox should not be able to run 64bit guest OSs on a Windows host anymore then it can on Ubuntu.

So can I get this working in Ubuntu? and if not.. What is different about the technology that allows Windows to run 64bit guests while Linux cannot?

---

### Post by SlugSlug on 2010-09-20
try update the bios -- most come with a utility that runs in windows and updates it auto

---

### Post by WorMzy on 2010-09-20
I dunno if this would make any difference -- I'm not particularly knowledgeable about VMs or their inner workings -- but is the Windows installation 64-bit? I'd expect a 64-bit OS to be able to run both 64-bit and 32-bit VMs, but I'd expect a 32-bit OS to only be able to run 32-bit VMs.

---

### Post by darthpenguin on 2010-09-20
> **SlugSlug said:**
> try update the bios -- most come with a utility that runs in windows and updates it auto

I checked and the BIOS is the most recent release. I had updated some time ago. I can't remember why but I'm sure there was a good reason :)

> I dunno if this would make any difference -- I'm not particularly knowledgeable about VMs or their inner workings -- but is the Windows installation 64-bit? I'd expect a 64-bit OS to be able to run both 64-bit and 32-bit VMs, but I'd expect a 32-bit OS to only be able to run 32-bit VMs.

I thought of that too. I couldn't remember if I installed 64 or 32 bit Windows. A quick check showed that the Windows 7 install is 32bit. So 32bit hosts can run 64bit guests but is that what the visualization is for? Is AMD-V needed when running a 64bit guest on 64bit host?

---

### Post by darthpenguin on 2010-10-09
OK. I've installed ubuntu 10.10 RC 64bit on my laptop and all works fine. it seems you can only run a 64 bit guest on a 64bit Linux host.

---

