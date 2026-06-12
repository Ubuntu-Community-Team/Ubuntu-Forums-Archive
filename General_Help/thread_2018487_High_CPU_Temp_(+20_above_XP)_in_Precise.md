---
title: "High CPU Temp (+20 above XP) in Precise"
date: 2012-07-06
forum: General Help
---

### Post by munkymac on 2012-07-06
I'm running 12.04 with Gnome Shell on a Samsung NC10, and my computer is running hot as hell. Because I have the option to dual boot (though I almost never use it) I've booted up in Windows too, for comparison.

Ubuntu: 78 Degrees Celsius (after 20 minutes from a cold start)
XP: 57 Degrees Celsius (after 20 minutes from a cold start)

After looking around on the internet, it seems that my model usually runs at about 35-38 degrees. So both of my values are quite high, which leads me to believe this is at least partially a hardware problem. But still, that extra 20 degrees is killing me...choppy video, huge lag opening programs, etc. 

Additionally (possibly a part of the same problem) it seems that my processor (Atom N270) is always running at 100 percent on one of the two cores (or hyperthreaded single core, I'm not quite sure how that shakes out) which I'm guessing shouldn't be the case. I'm at a loss for what to do. 

I'm not sure what would be helpful to post, so here is the output of Sensors:
```
aaron@aaron-NC10:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +76.0°C  (crit = +98.0°C)

```

and cpufreqinfo:
```
aaron@aaron-NC10:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.
  cpufreq stats: 1.60 GHz:19.39%, 1.33 GHz:0.54%, 1.07 GHz:56.68%, 800 MHz:23.40%  (7620)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.
  cpufreq stats: 1.60 GHz:22.86%, 1.33 GHz:0.19%, 1.07 GHz:66.73%, 800 MHz:10.23%  (2823)

```

---

