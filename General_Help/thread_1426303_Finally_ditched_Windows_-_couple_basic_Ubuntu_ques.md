---
title: "Finally ditched Windows - couple basic Ubuntu questions"
date: 2010-03-10
forum: General Help
---

### Post by jm27 on 2010-03-10
I have finally ditched Windows after using it for, well, too long. I've been running various flavors of Linux on servers, routers, and utility boxes for some time now, but never in a desktop environment. I finally decided that I need to make the switch eventually, as I can't stand Windows 7, and the sooner I do so, the better.

Short of VMWare sessions, my entire house is now Windows free.

I'm running into two basic issues that I can't seem to resolve through the search engine. The issues in question relate to an x86_64 installation of 9.10.


First and foremost, I cannot seem to get the CPU frequency scaling to work properly with an overclocked processor. The scaling itself is a good powersaving feature that I would like to retain, however when I have it enabled, the on demand scaling will only scale up to the stock clock speed of the processor.

The CPU scaling applet reports and maxes out at 2.66GHz, which is the stock clock, although it has been configured in the BIOS to go up to 3.4GHz. I can hit 3.4 with scaling completely off, or through Windows, but Ubuntu will not scale up to 3.4 on demand, which is a huge problem - it is as if I'm missing one core out of four (27% performance hit).


The second, and less critical issue, is my apparent inability to find a decent GUI archiver. File roller is fine for extraction, but lacks advanced options for compressing either from a running instance or the shell. Windows has spoiled me in allowing for easy configuration of compression parameters, depending on whether I need to use an archiver to combine files, whether I need quick compression, or whether I need maximum compression for a repeatedly downloaded file or cold storage of backups.

I'm losing WinRAR's ability to add integrated recovery data, which is bad enough, but losing a decent file archiver is wanting to make me bring the Windows back out of convenience. CLI compression is simply not an efficient way to work on a desktop system, when so much of what I do involves archive manipulation.

Thanks in advance.

---

### Post by shriramrs31 on 2010-03-10
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

This file indicates all the available frequencies your processor can handle (according to the kernel).

normally CPU max freq is given by BIOS to OS. So linux kernel / windows has no difference. If you have selected properly in BIOS overclocking speed, you should see it in the above file.

---

### Post by shriramrs31 on 2010-03-10
I read your post more clearly now and it seems you are hitting 3.4 with scaling off from applet. is this right ?

If you are not hitting 3.4 on demand, may be the CPU load is not big enough to increase the demand to 3.4GHz.

try this "http://weather.ou.edu/~apw/projects/stress/" stress is actually part of repository, so you shoud be able to install with apt-get or synaptic.

example : "sudo stress -v --cpu 2" should load your two cores. In mine the CPU scaling policy is "on demand" and after this command, both the cores rises from 800MHz to 2.1GHz

---

### Post by jm27 on 2010-03-10
The available frequencies are showing as:
```

2661000 2660000 2527000 2394000 2261000 2128000 1995000 1862000 1729000 1596000 1463000 1330000 1197000

```

for CPUs 0-3.

The expected OC value of 3.4GHz shows both in the BIOS and CPUZ on Windows, using BIOS settings which have remained unchanged across my testing.

These are identical to the stock frequencies which should be reported for this processor, even though the processor is not running at stock per the BIOS.

The problem is only manifesting under Ubuntu with scaling not disabled completely.

---

### Post by jm27 on 2010-03-10
> **shriramrs31 said:**
> I read your post more clearly now and it seems you are hitting 3.4 with scaling off from applet. is this right ?

If you are not hitting 3.4 on demand, may be the CPU load is not big enough to increase the demand to 3.4GHz.

try this "http://weather.ou.edu/~apw/projects/stress/" stress is actually part of repository, so you shoud be able to install with apt-get or synaptic.
No, the problem is that the applet should be hitting up to 3.4 (the OC) on demand, when the system needs it, or when so configured, but the applet only goes up to the stock of 2.66, in accordance with the available frequencies per the dump of the available frequencies from the device.

The 3.4 under Ubuntu came in when I completely kill the CPU management entirely, which defeats the benefit of being able to scale back when full speed is not needed.

Anything above stock is not even an option for manual selection or in performance mode.

I've got all four cores maxed with F@H during testing so there should be no issue of too little load.

---

