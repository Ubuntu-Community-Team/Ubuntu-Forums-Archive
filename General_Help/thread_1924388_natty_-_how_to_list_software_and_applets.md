---
title: "natty - how to list software and applets?"
date: 2012-02-12
forum: General Help
---

### Post by qwertyjjj on 2012-02-12
How can I add applets to the top gnome panel in Natty?
I used to have one showing cpufreq there but it has gone now.
Edit: cpufreq is installed but it won;t start!
```

jason@Inspiron-9300:~$ indicator-cpufreq
Traceback (most recent call last):
  File "/usr/bin/indicator-cpufreq", line 81, in <module>
    ind = MyIndicator()
  File "/usr/lib/python2.7/dist-packages/indicator_cpufreq/indicator.py", line 95, in __init__
    self.update_ui()
  File "/usr/lib/python2.7/dist-packages/indicator_cpufreq/indicator.py", line 106, in update_ui
    fmin, fmax, governor = cpufreq.get_policy(self.cpus[0])
  File "/usr/lib/python2.7/dist-packages/indicator_cpufreq/cpufreq.py", line 143, in get_policy
    policy = (p.contents.min, p.contents.max, p.contents.governor)
ValueError: NULL pointer access


jason@Inspiron-9300:~$ sudo /etc/init.d/cpufrequtils start
 * CPUFreq Utilities: Setting ondemand CPUFreq governor...                       * disabled, governor not available...                                   [ OK ] 
jason@Inspiron-9300:~$ 


```

jason@Inspiron-9300:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
jason@Inspiron-9300:~$

---

### Post by qwertyjjj on 2012-02-13
Any ideas how to get it up to full speed?
I've seen a few bug reports on this Natty but it's supposed to be fixed in Ocelot (which I have now installed).
Also, I saw some suggesting to set grub to bypass the BIOS but that doesn;t seem to work either.

---

### Post by bluexrider on 2012-02-13
> **qwertyjjj said:**
> Any ideas how to get it up to full speed?
I've seen a few bug reports on this Natty but it's supposed to be fixed in Ocelot (which I have now installed).
Also, I saw some suggesting to set grub to bypass the BIOS but that doesn;t seem to work either.

Natty vs Oclot, 2 different versions of Gnome. I doubt the settings will remain the same.

You need the BIOS in order to load the OS.
I don't think any of the protected mode operating systems make any reference to BIOS code once the system is up and running.

---

### Post by qwertyjjj on 2012-02-13
> **bluexrider said:**
> Natty vs Oclot, 2 different versions of Gnome. I doubt the settings will remain the same.

You need the BIOS in order to load the OS.
I don't think any of the protected mode operating systems make any reference to BIOS code once the system is up and running.

I meant it bypasses the BIOS for 1 setting, it;s called something pp... specifically for the CPU speed.

---

### Post by bluexrider on 2012-02-13
There may be a application to read the cpu speed and modify some settings however I am not aware as how to 'bypass' the BIOS

---

### Post by qwertyjjj on 2012-02-13
> **bluexrider said:**
> There may be a application to read the cpu speed and modify some settings however I am not aware as how to 'bypass' the BIOS

I think it is adding a line to the grub file with processor.ignore_ppc = 1

However, it hasnlt helped:

j@j-Inspiron-9300:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 75.0 MHz - 600 MHz
  available frequency steps: 75.0 MHz, 150 MHz, 225 MHz, 300 MHz, 375 MHz, 450 MHz, 525 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: f**requency should be within 75.0 MHz and 600 MHz.**
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz.
  cpufreq stats: 75.0 MHz:0.00%, 150 MHz:0.00%, 225 MHz:0.00%, 300 MHz:0.00%, 375 MHz:0.00%, 450 MHz:0.00%, 525 MHz:0.00%, 600 MHz:100.00%
(arg: 2)

---

