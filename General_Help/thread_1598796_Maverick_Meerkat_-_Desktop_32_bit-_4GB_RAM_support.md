---
title: "Maverick Meerkat - Desktop 32 bit- 4GB RAM support"
date: 2010-10-17
forum: General Help
---

### Post by ozzyprv on 2010-10-17
Does anybody know if Maverick Meerkat (Desktop 32 bit flavor) supports more than 3 GB of RAM?
Thanks.

---

### Post by soldier1st on 2010-10-17
32bit systems are limited to 4GB but if your cpu has pae support then installing a pae kernel will allow access to more memory.

---

### Post by garvinrick4 on 2010-10-17
install 32 bit if it is detected 4 gig and over it will install pae, if it does not, not supported.

---

### Post by soldier1st on 2010-10-17
go to terminal and copy and past this cat /proc/cpuinfo | grep flags it will list your cpu capabilities and if you don't see pae anywhere then your cpu does not support it.

---

### Post by sendblink23 on 2010-10-17
If your CPU supports PAE you should see something like this:
```
sendblink23@sendblink23-MS-7577:~$ cat /proc/cpuinfo | grep flags
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save

```
*Note mine is a quadcore that is why you see the things repeated 4 times

---

### Post by ozzyprv on 2010-10-17
Thank you all.

This is what I got, so I am assuming that this CPU supports PAE.
```
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority

```

Any hint or pointers on how to "enable" PAE?

Thanks again.

---

### Post by tgm4883 on 2010-10-17
whats the output of 
```
uname -a
```

---

### Post by ozzyprv on 2010-10-17
> **tgm4883 said:**
> whats the output of 
```
uname -a
```

The output is:
> Linux mybox02 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

---

### Post by tgm4883 on 2010-10-17
> **ozzyprv said:**
> The output is:

You don't have a pae kernel running. You don't have a 10.10 kernel running either. That's a 10.04 kernel.

---

### Post by ozzyprv on 2010-10-17
Right and right.

I was asking about 10.10 to check if it was worthy to move on to the newer version. If it has the support for 4 GB for 32 bits by defaults I am willing to make the move.

Now, it seems like I could enable the PAE even at 10.04.

---

### Post by gmargo on 2010-10-17
Install the **linux-generic-pae** package to run the pae-enabled kernel.

[http://packages.ubuntu.com/lucid/linux-generic-pae]("http://packages.ubuntu.com/lucid/linux-image-generic-pae")
[http://packages.ubuntu.com/maverick/linux-generic-pae]("http://packages.ubuntu.com/maverick/linux-image-generic-pae")

---

### Post by shimanotaka on 2010-11-05
Halp! I checked my processor specs and installed pae according to the instructions in this thread, but after the reboot I get only command prompt! How do I get my computer to boot into GUI again?

EDIT: I found the reason. At the prompt it didn't say anything special.
Then I tried
**sudo /etc/init.d/gdm start**
but it said it was already started.
So I tried
**sudo /etc/init.d/gdm restart**
and then I got a bunch of errors, saying it couldn't find **fglrx**.
So I went into recovery mode and re-installed fglrx and after that it worked fine and the system monitor shows that I have 3.7GB RAM instead of 3.2GB. Yay!

---

### Post by alanmoore78 on 2010-11-20
And that's what I just did.  I swapped a 1GB chip for a 2GB chip and now I had 4GB in Bios and Windows 7HP64.  Still saw 2.9GB in Ubuntu.  So I installed the PAE-enabled kernel, restarted, and now I see 3.9GB.  Simple as that.

Thank you to all in the forums who are aware of all these simple little fixes and workarounds and are able to help those of us who understand little about kernels and limits and all that!

---

### Post by puterg33k on 2011-06-14
Hello all, I'm having trouble with compiz/awn/emerald. 

I did this install: sudo apt-get install linux-generic-pae 
It worked, and now my system recognises my 6GB RAM, however; now my gnome/compiz/awn/emerald went kablewy... lol

Any help would be great!

---

### Post by uRock on 2011-06-14
Please create a new thread for your emerald issue.

Thread Closed

---

