---
title: "HOW TO? - Turbo Boost in Ubuntu 3.2.0-23-generic"
date: 2012-05-06
forum: General Help
---

### Post by lightninhopkins on 2012-05-06
I've been using a pair of the new E5-2690 Intel CPU's, and in Windows the Turbo Boost is working, however, in CentOS, MacOS (hack), and Ubuntu, there is no sign of Turbo Boost being used. In Win7 the boost goes up to 3.8GHz. Geekbench is at 40K for win and 35K for this ubuntu install. 

I've installed cpufreq-info, and it shows the info below. 

Any ideas on how to get Turbo Boost working? I don't even have any use for this stuff, just need to get it working because the voices tell me not to quit till it's right :)

--------------------------------------------------------------------------------
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 1.20 GHz - 2.90 GHz
  available frequency steps: 2.90 GHz, 2.90 GHz, 2.80 GHz, 2.70 GHz, 2.50 GHz, 2.40 GHz, 2.30 GHz, 2.20 GHz, 2.00 GHz, 1.90 GHz, 1.80 GHz, 1.70 GHz, 1.60 GHz, 1.40 GHz, 1.30 GHz, 1.20 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.20 GHz and 2.90 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.
  cpufreq stats: 2.90 GHz:4.96%, 2.90 GHz:0.00%, 2.80 GHz:0.00%, 2.70 GHz:0.00%, 2.50 GHz:0.00%, 2.40 GHz:0.00%, 2.30 GHz:0.00%, 2.20 GHz:0.00%, 2.00 GHz:0.00%, 1.90 GHz:0.00%, 1.80 GHz:0.00%, 1.70 GHz:0.00%, 1.60 GHz:0.03%, 1.40 GHz:0.00%, 1.30 GHz:0.00%, 1.20 GHz:95.01%  (57)
--------------------------------------------------------------------------------

---

### Post by lightninhopkins on 2012-05-09
wondering if anyone had any info.

---

### Post by deltaprojects on 2012-09-15
I'm not sure how to get turbo boost working, but I sure am interested how to get cpufreq-info/-set to work with the new e5 procs.

What type of server do you use? We have a bunch of Dell R620 and R720, but cpufreq-info just says:


```
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.

```

We're running kernel 3.2.0.30 on ubuntu 12.04.1.

---

### Post by Epodx64 on 2012-09-15
Try downloading a cpu frequency app and adjust it from ondemand to performance 

sudo apt-get install indicator-cpufreq

or some similar type program

---

### Post by jerrrys on 2012-09-15
I don't use TurboBoost, but here's a link that may help

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Turbo+Boost&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Turbo+Boost&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

