---
title: "CpuFrequency Selector help"
date: 2010-07-24
forum: General Help
---

### Post by FAJALOU on 2010-07-24
Hey Folks,
        I am really close to getting frequency scaling to work.  I have it finally set up.  However two of the modes seem to not be working.  Whenever I try to choose "On Demand" or "Conservative" the mode is automatically switched to "performance."  Both the "Performance" and "Power Save" modes work great.  I can also choose different options, such as 1.8 Ghz or as low as 299 Mhz.  Even if I put in 
```
sudo cpufreq-set -g ondemand


```

Doesn't even seem to work, but I don't know how to look to see if it IS actually working?

Any help appreciated! Thanks!

---

### Post by dcstar on 2010-07-24
> **FAJALOU said:**
> Hey Folks,
        I am really close to getting frequency scaling to work.
........

Huh?, "Frequency Scaling" works out of the box, there is nothing to get "to work".

Add the Frequency Scaling Applet to a panel and you can see it working and set it as required.

---

### Post by FAJALOU on 2010-07-24
Well that would be really nice...... but it's not working for me.  Lol the only way I can get it to work is by using the p4_clockmod.



Even if I put in:
```
$ sudo cpufreq-set -g ondemand

```

The applet does not change.  In fact if I put in the last code and my frequency is set to 1.2 Ghz, for example, the applet switches to "performance."  So is this a bug?  The same thing happens if I put in "conservative" but power save seems to be working.

Here is my /etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

p4_clockmod
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
lp
```

---

### Post by FAJALOU on 2010-08-04
Bump?

---

### Post by FAJALOU on 2010-08-04
Just as a note:

louie@lrc-laptop:~$ cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 300 MHz - 2.40 GHz
  available frequency steps: 300 MHz, 600 MHz, 900 MHz, 1.20 GHz, 1.50 GHz, 1.80 GHz, 2.10 GHz, 2.40 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.50 GHz and 1.50 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 1.50 GHz.
louie@lrc-laptop:~$ 


However, the gnome-applets still says 1.80 Ghz....
Help?

---

### Post by FAJALOU on 2010-08-04
Ok.... so I am very close.  Right now I can set everything via command line.... but the applet STILL says 1.80 Ghz!


louie@lrc-laptop:~$ sudo cpufreq-set --min 299000
louie@lrc-laptop:~$ sudo cpufreq-set --max 240000000
louie@lrc-laptop:~$ sudo cpufreq-set -f 299000
louie@lrc-laptop:~$ sudo cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 300 MHz - 2.40 GHz
  available frequency steps: 300 MHz, 600 MHz, 900 MHz, 1.20 GHz, 1.50 GHz, 1.80 GHz, 2.10 GHz, 2.40 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 300 MHz and 2.40 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 300 MHz (asserted by call to hardware).
louie@lrc-laptop:~$ sudo cpufreq-set -g powersave
louie@lrc-laptop:~$ sudo cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 300 MHz - 2.40 GHz
  available frequency steps: 300 MHz, 600 MHz, 900 MHz, 1.20 GHz, 1.50 GHz, 1.80 GHz, 2.10 GHz, 2.40 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 300 MHz and 2.40 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 300 MHz (asserted by call to hardware).
louie@lrc-laptop:~$ sudo cpufreq-set -g conservative
louie@lrc-laptop:~$ 

So I removed the applet and added a new one, and low and behold it worked.... up to the point where I tried to change it to anything, just like I say in the first post....

----

Just noticed this in my "messages"
Jul 26 23:49:16 lrc-laptop kernel: [ 1851.470267] conservative governor failed, too long transition latency of HW, fallback to performance governor
Jul 26 23:49:20 lrc-laptop kernel: [ 1855.367233] ondemand governor failed, too long transition latency of HW, fallback to performance governor

So how to fix that?

---

