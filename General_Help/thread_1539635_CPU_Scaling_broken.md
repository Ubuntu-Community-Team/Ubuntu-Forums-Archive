---
title: "CPU Scaling broken"
date: 2010-07-26
forum: General Help
---

### Post by Ingenium on 2010-07-26
I have a Core 2 Duo T9600. I noticed video playing performance has been really bad lately, and videos that used to work fine now stuttered. I would say it started happening 2-3 weeks ago. I discovered the culprit is that the CPU is scaling down to 800Mhz and sticking there.

Running cpufreq-info yields:

```
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.80 GHz
  available frequency steps: 2.80 GHz, 2.80 GHz, 2.13 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.80 GHz:8.52%, 2.80 GHz:1.03%, 2.13 GHz:1.03%, 1.60 GHz:1.55%, 800 MHz:87.88%  (2403)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.80 GHz
  available frequency steps: 2.80 GHz, 2.80 GHz, 2.13 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.80 GHz:8.07%, 2.80 GHz:0.78%, 2.13 GHz:0.92%, 1.60 GHz:1.19%, 800 MHz:89.04%  (2176)

```

Notice that current policy is "frequency should be within 800 MHz and 800 MHz." It will sometimes switch to the correct "frequency should be within 800 MHz and 2.80 GHz." but never when it's actually under high load. If I start doing anything CPU intensive, it immediately drops to 800MHz, but when I stop it allows 2.8GHz again. 

I tried manually setting the governor to performance, but it also gives the same frequency range before somehow changing back to ondemand on its own. When I try to force it to 2.8GHz, it doesn't apply and just stays at 800MHz.

Switching kernels to older versions didn't fix it. 

Anyone have any ideas?

---

### Post by adrien214 on 2010-10-31
maybe you can try to edit 

**scaling_max_freq **

in 

**/sys/devices/systewm/cpu/cpu*/cpufreq**

 I have noticed that when I upgraded to Maverick, the min_freq and max_freq where the same. My problem is that the cpu is now stuck to max_freq...

---

### Post by dcstar on 2010-11-01
> **Ingenium said:**
> 
...........
Switching kernels to older versions didn't fix it. 

Anyone have any ideas?

Try installing the **powernowd** package.

---

### Post by jonsson on 2011-01-18
> **adrien214 said:**
> maybe you can try to edit 

**scaling_max_freq **

in 

**/sys/devices/systewm/cpu/cpu*/cpufreq**

 I have noticed that when I upgraded to Maverick, the min_freq and max_freq where the same. My problem is that the cpu is now stuck to max_freq...

I've been googling for hours and this looked like the most promising suggesting yet. However, when I tried this and rebooted it was back to 800 Mhz again :(

Has anyone found some kind of solution yet?

---

### Post by pqwoerituytrueiwoq on 2011-01-18
I had an issue with a system not using it's full power there was a thing in the bios called speedstep limiting it to 800 MHz
there may be something in the thread i made looking for help [http://ubuntuforums.org/showthread.php?t=1618442](http://ubuntuforums.org/showthread.php?t=1618442) if that is not your issue

---

### Post by jonsson on 2011-01-19
Hm, I think my fan might actually be broken, causing overheating. I just opened up the laptop and tried to clean the fan (not that it looked dirty) and after that it was running at 2 GHz. I think it was just because it had had some time to cool down, though, because it has now reverted to running at 800 MHz and I could never hear the fan running. Looks like I will have to take it out and have a closer look and probably replace it. Too bad I said no when Dell called me a few months ago to ask if I wanted to pay for extended warranty. :|

I currently have a Windows partition as well and the machine seemed really slow when I booted that too, even if I have no CPU meter installed there.

Shouldn't there be a message about overheating and forced throttling logged somewhere? Where should I look for that?

---

### Post by mc4man on 2011-01-19
> Shouldn't there be a message about overheating and forced throttling logged somewhere? 
It's possible that you're overheating during the boot, then you'd be locked at the lowest speed for the life of the session even if the temps dropped to acceptable. (till a restart where the same will happen again
There may be something in one of the /var/log log files.

(had this happen here w/ my son's laptop - took awhile to figure out, having the fan unit replaced solved it.

---

