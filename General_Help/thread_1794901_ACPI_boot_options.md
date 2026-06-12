---
title: "ACPI boot options"
date: 2011-07-01
forum: General Help
---

### Post by caffeinated blood on 2011-07-01
Looking in System Monitor recently I saw that my CPU usage was rather high(in the low 20% for average use). After some research I found that ACPI may be the problem. I used the 'acpi=off' boot command from Boot Options List/Ubuntu and my CPU usage dropped to a very acceptable level. Any ACPI errors I had in logging are no longer occurring. So I ask all - Should I continue to use this boot command or should I also try others from the Boot Options List? And does disabling ACPI risk any possible system hardware damage?

---

### Post by prodigy_ on 2011-07-01
ACPI manages (among other things) power/performance states of the CPU. Turning ACPI off won't damage anything.

---

### Post by JC Cheloven on 2011-07-01
acpi=off completely disables acpi, which  is only recommended for BIOSes older than 2000. For newer bios-es it is better advised
```
pci=routeirq
```
or
```
pci=noacpi
```

I'd try one of these to see if that fixes your cpu issue.

---

### Post by caffeinated blood on 2011-07-01
My system board is only one year old on a home build so I guess I'll give the other boot option(s) a shot. Thanks.

---

### Post by caffeinated blood on 2011-07-01
Sorry, I should have tried 'pci=routeirq' and 'pci=noacpi' before I posted a reply. Tried both - both returned the ACPI errors I was seeing and actually put my cpu usage past 50% during normal use! Is the 'acpi=off' really not recommended for my board?

---

### Post by wildmanne39 on 2011-07-02
> **caffeinated blood said:**
> Sorry, I should have tried 'pci=routeirq' and 'pci=noacpi' before I posted a reply. Tried both - both returned the ACPI errors I was seeing and actually put my cpu usage past 50% during normal use! Is the 'acpi=off' really not recommended for my board?
Hi, I believe you need to be careful when turning off acpi, it is used for many things depending on your system, I think it even controls the fans in some systems, so I would make sure your fans are still working.

---

### Post by prodigy_ on 2011-07-02
> **caffeinated blood said:**
> Tried both - both returned the ACPI errors I was seeing
What did those errors say?

---

### Post by JC Cheloven on 2011-07-02
As prodigy_ states, to know what the errors say could be of help.

In the meanwhile, you can try these old couple of parameters to boot with. They're meant to overcome blockings and other hardware issues due to (supposedly) poor/buggy bios implementations:
```
noapic nolapic
```
(please try passing *both* parameters to the kernel at boot time).

---

### Post by caffeinated blood on 2011-07-02
The ACPI errors I am seeing are '(psargs-0359):[ECEN]Namespace lookup failure,AE_NOT_FOUND'  '(psparse-0537):Method parse/execution failed[\]'  '(dswload-0659):[PCI0]Namespace lookup failure'  '(uteval-0250):Method execution failed[\SECD.S_01._STA]' one other item I'm not sure of 'ACPI Exception AE_NOT_FOUND No handler for Region[SACS]'. In my research I saw that these are reported bugs. I tried the other 2 boot commands together 'noapic nolapic' and still seeing the errors and high CPU use. With the 'acpi=off' command and others my system fans are still spinning, but I have no way to monitor their actual r.p.m. - seems like they are going full tilt.                                                                                                                                      One last note; I updated my BIOS a few weeks back because I also saw the errors with the previous BIOS version - no change whatsoever.

---

### Post by JC Cheloven on 2011-07-03
Mhhh... well, using acpi=off and waiting for the best is always an option, I guess. 

I'm afraid I'm not familiar with the output of these errors, so I can't help much on that :/

---

### Post by caffeinated blood on 2011-07-03
If those errors are reported bugs does that suggest I have to live with them? As many as I saw reported while googling I would think maybe a fix in the kernel would be needed. Or is it just that motherboard manufacturers/bios updates are simply not supporting linux? And I've got to ask again after reading wildmanne39's post; is it really safe for my system(motherboard much newer than 2000) to be running with 'acpi=off'?

---

### Post by prodigy_ on 2011-07-03
> **caffeinated blood said:**
> If those errors are reported bugs does that suggest I have to live with them?
Try to report them yourself (don't forget to attach relevant pieces of logs) and see what happens. You'll probably be asked to run some commands like **dmidecode**.

Such issues are usually resolved sooner or later but if you'll open a bugreport and supply enough information, "sooner" will become a bit more likely. :)

---

### Post by wildmanne39 on 2011-07-04
> **caffeinated blood said:**
> If those errors are reported bugs does that suggest I have to live with them? As many as I saw reported while googling I would think maybe a fix in the kernel would be needed. Or is it just that motherboard manufacturers/bios updates are simply not supporting linux? And I've got to ask again after reading wildmanne39's post; is it really safe for my system(motherboard much newer than 2000) to be running with 'acpi=off'?
Hi, usually you can use that option to boot and then fix your problem quickly and you do not make that option permanent. Have you looked into your video card driver that is a likely candidate for causing your problem, and here is a quote of the warning for turning off acpi.

> acpi=off
This disables ACPI completely.
Note: this may not work with all computers and will disable a lot of useful (or even needed) features. In some cases it may even disable some crucial features, like.. fans. Be careful with this option, it might cause your machine to overheat if the fans no longer turn. Think of this as a last resort. Also note some machines require acpi=ht instead.This the link to that forum.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by caffeinated blood on 2011-07-04
I don't believe the video card driver is having an effect because I reinstalled Ubuntu(10.04/32 bit)after I updated my BIOS and saw the same ACPI errors on the initial reboot using the Nouveau driver before replacing it with nVidia's driver. One last resort - Would it be wise to try other boot command options('apm=off' 'acpi=force' acpi=ht' 'acpi_irq_balance/nobalance')??????

---

### Post by wildmanne39 on 2011-07-04
> **caffeinated blood said:**
> I don't believe the video card driver is having an effect because I reinstalled Ubuntu(10.04/32 bit)after I updated my BIOS and saw the same ACPI errors on the initial reboot using the Nouveau driver before replacing it with nVidia's driver. One last resort - Would it be wise to try other boot command options('apm=off' 'acpi=force' acpi=ht' 'acpi_irq_balance/nobalance')??????
Hi, yes it would be better to try the other options before turning  of acpi completely.

---

