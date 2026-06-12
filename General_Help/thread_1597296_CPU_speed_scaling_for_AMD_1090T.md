---
title: "CPU speed scaling for AMD 1090T?"
date: 2010-10-15
forum: General Help
---

### Post by gorbalad on 2010-10-15
I'm running ubuntu 10.10 64 bit. CPU speed scaling says my CPU (AMD PhenomII 1090T) is not supported, and shows full speed on all cores, regardless of load. I've read that those issues were solved in kernel 2.6.34...

How can I make it work? or do I have to wait for an update?

Motherboard is an ASUS Crossfire IV.


Admins: Feel free to shift this post to another (sub-)forum if necessary, I wasn't sure where to put it.

---

### Post by gorbalad on 2010-10-19
```

dmesg|grep powernow
[    2.585619] powernow-k8: Found 1 AMD Phenom(tm) II X6 1090T Processor (6 cpu cores) (version 2.20.00)
[    2.585640] powernow-k8: Core Performance Boosting: on.
[    2.585644] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    2.585645] [Firmware Bug]: powernow-k8: Try again with latest BIOS.

```my current BIOS version is 1005, now there is 1102, so I'll try that and report back...

---

### Post by gorbalad on 2010-10-19
patching the bios was easy, but had no effect on this. the output of dmesg|grep powernow remains unchanged.

---

### Post by happyhamster on 2010-10-19
Is Cool&Quiet perhaps disabled in the BIOS? Frequency scaling is working fine for me on Maverick (2.6.35 or 2.6.36-rc8). See:
```

dmesg | grep powernow
[    1.387840] powernow-k8: Found 1 AMD Phenom(tm) II X6 1055T Processor (6 cpu cores) (version 2.20.00)
[    1.387846] powernow-k8: Core Performance Boosting: on.
[    1.387867] powernow-k8:    0 : pstate 0 (2800 MHz)
[    1.387868] powernow-k8:    1 : pstate 1 (2200 MHz)
[    1.387869] powernow-k8:    2 : pstate 2 (1500 MHz)
[    1.387870] powernow-k8:    3 : pstate 3 (800 MHz)

```

---

### Post by gorbalad on 2010-10-20
yep, it was turned off. I could have sworn that I turned it on, but maybe it was disabled by one of the BIOS-updates. now I get the expected output:
```
dmesg|grep powernow
[    2.595565] powernow-k8: Found 1 AMD Phenom(tm) II X6 1090T Processor (6 cpu cores) (version 2.20.00)
[    2.595575] powernow-k8: Core Performance Boosting: on.
[    2.595596] powernow-k8:    0 : pstate 0 (3200 MHz)
[    2.595597] powernow-k8:    1 : pstate 1 (2400 MHz)
[    2.595598] powernow-k8:    2 : pstate 2 (1600 MHz)
[    2.595599] powernow-k8:    3 : pstate 3 (800 MHz)
```

what I do not yet get is the switching between those states, at least not according to the CPU Frequency Scaling Monitor 2.30.0 (the gnome-applet-thingy), which did work on all my previous athlons...

---

### Post by TBABill on 2010-10-20
I'm not sure it'll work, but have you tried to install cpufreq-utilities? Find it in Synaptic and install. Works the same way. But to get it to work: ```
cpufreq-set --governor ondemand
```
 
To check what state it is running in after that, just use: ```
cpufreq-info
```
 
Only offering this because you said the applet isn't managing it correctly. I thought in 10.04 and 10.10 that ondemand (or powersave) was default?! Why it's not working on such a new processor is troubling.

---

### Post by gorbalad on 2010-10-20
the ondemand setting is active in that applet, but it always shows full speed, even when running no programs at all (besides all the background stuff, obviously. but that does not occupy any core with more than maybe 15% peaks, well below 10% on average)

I have installed that cpu-freq stuff already, since I wasn't sure about the name for the package I wanted. Gotta try it.

---

### Post by TBABill on 2010-10-20
Not a prob. I found a deep love of using CPUFREQ in PCLinuxOS when it didn't manage heat well. Lots of searching to find out exactly how best to use it. Now with the new kernels it seems a non issue but since yours borked on the setting I'm curious what the cause is and what the fix is that works. 10.10 is an odd beast right now so I am cautiously watching (and reverted 2 machines back to 10.04). Post back if it works.

---

### Post by gorbalad on 2010-10-20
I've learned to wait for a few weeks before I upgrade ubuntu. but this is a new machine, and I've already waited a few weeks for 10.10, to avoid the upgrade process and wear on my system ssd, so the temptation to install it soon was quite big :)

---

### Post by gorbalad on 2010-10-21
I also switched on C1E in the bios, maybe that causes problems as well. I'll have to experiment a little...

---

### Post by TBABill on 2010-10-21
I'm not familiar with the term C1E. Is that something for your fans?

---

### Post by gorbalad on 2010-10-21
frankly, I'm not sure what C1E does, but google suggests that it is related to cool'n'quiet. 
anyway, it made no difference at all. I turned off C1E, and tried cpufreq:
```
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 8.0 us.
  hardware limits: 800 MHz - 3.20 GHz
  available frequency steps: 3.20 GHz, 2.40 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 3.20 GHz and 3.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 3.20 GHz.
  cpufreq stats: 3.20 GHz:99.90%, 2.40 GHz:0.00%, 1.60 GHz:0.00%, 800 MHz:0.10%  (2)
```(looks the same for the other 5 cores)
So I'm still on full speed, regardless of load.

---

### Post by gorbalad on 2010-11-01
it was probably too simple.

```
sudo cpufreq-set -c 5 -d 800MHz -u 3200MHz 
```
this sets the lower limit to 800MHz and the upper limit to 3200MHz on cpu 5. do that for cpus 0-5, and everything looks fine. I just hope it still works after a reboot :D

---

### Post by gradinaruvasile on 2010-11-01
Put it in a startup script (system startup, not GUI).

---

### Post by gorbalad on 2010-11-02
indeed, that was necessary. I wonder what happened there, this worked completely out of the box on the other 3 machines (dualcore athlons with 2 and 2.5GHz, running ubuntu 8.04 to 10.04)

---

### Post by gradinaruvasile on 2010-11-02
Well then it is surely related to the changes made for 10.10. You should file a bug.

---

### Post by gorbalad on 2010-11-02
well, it could also be due to the new CPU, I've read about some trouble with setting frequencies on the 1090T right, but thought everything was fixed with the 2.6.35 kernel. I'm also still waiting to see it to use turbocore (clocking cores higher than 3.2GHz when not all 6 are needed)...

---

