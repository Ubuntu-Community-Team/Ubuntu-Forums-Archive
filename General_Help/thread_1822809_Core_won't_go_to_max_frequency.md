---
title: "Core won't go to max frequency"
date: 2011-08-11
forum: General Help
---

### Post by ravij96 on 2011-08-11
Hi I have a dual core processor. I don't really know much about this but I always used the frequency applet to set the cores speed to what I want to avoid over heating. I was always able to set both cores to 2.10GHz, which is the max, but now the first core refuses to go above 1.68 GHz. If I type in 

cpufreq-info

I get

cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 1000 ns.
  hardware limits: 525 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 1.05 GHz, 525 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 525 MHz and 1.68 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 525 MHz.
  cpufreq stats: 2.10 GHz:0.02%, 1.05 GHz:30.28%, 525 MHz:69.70%  (34697)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 1000 ns.
  hardware limits: 525 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 1.05 GHz, 525 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 525 MHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 525 MHz.
  cpufreq stats: 2.10 GHz:31.52%, 1.05 GHz:5.02%, 525 MHz:63.46%  (15176)

So please can someone help me.

---

### Post by ravij96 on 2011-08-11
Problem fixed itself

---

