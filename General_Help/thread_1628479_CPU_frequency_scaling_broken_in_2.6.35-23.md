---
title: "CPU frequency scaling broken in 2.6.35-23 ?"
date: 2010-11-22
forum: General Help
---

### Post by thiese on 2010-11-22
After upgrading to kernel 2.6.35-23 cpu freq scaling on my Intel core duo 2 wasn't working anymore, was stuck at 800mhz despite setting it manually to a higher treshold or setting the performance governor. The kernel modules loaded ok (tried acpi-cpufreq and the speedstep-centrino although I thought they're the same) and the only thing in my log was:
```
Nov 22 22:32:14 thies-laptop cpufreqd: cpufreqd_set_profile     : Couldn't set profile "Performance High" set for cpu0 (22010
00-2201000-performance)
Nov 22 22:32:14 thies-laptop cpufreqd: cpufreqd_loop            : Cannot set policy, Rule unchanged ("none").

```
Going back to 2.6.35-22 fixed everything, is this a known issue with 35-23?

---

### Post by Decatf on 2010-11-22
Stick with 2.6.35.22 unless you had a specific reason for using 2.6.35-23 from the proposed repository.

---

### Post by mciverza on 2010-12-02
Linux shrooms 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

I am using Lucid 64-bit with 2.6.34-24 kernel and I have started getting the same behaviour. after an indeterminate time > 10 mins my CPU cores lock at 800MHz

My CPU is Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz

and cpufreq-info returns: 
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.20 GHz:0.57%, 2.20 GHz:0.01%, 1.60 GHz:0.00%, 1.20 GHz:0.00%, 800 MHz:99.42%  (8)

---

### Post by mc4man on 2010-12-02
> after an indeterminate time > 10 mins my CPU cores lock at 800MHz
I'd ck. the cpu temps starting right after boot and then fairly often while putting some stress on the cpu.
If it reaches a 'scale down' level then the speed will lock at lowest for remainder of session (even if temp returns to normal or thereabouts

---

### Post by Dr4K4n on 2011-06-07
Hello Guys,

any new solutions for the problem ?

I'm facing the same issue of being stuck at 800 Mhz after a while. I've got a Thinkpad R500 with an "Intel(R) Core(TM)2 Duo CPU     P8400 @ 2.26GHz".

I recently moved from Ubuntu 10.04 LTS to 11.04, but the issue is still present...

Thanks!

---

