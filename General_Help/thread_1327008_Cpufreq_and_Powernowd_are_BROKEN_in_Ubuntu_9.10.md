---
title: "Cpufreq and Powernowd are BROKEN in Ubuntu 9.10"
date: 2009-11-15
forum: General Help
---

### Post by Regeneration on 2009-11-15
I would like to report that both cpufreq and powernowd aren't working in Ubuntu 9.10. 

• The governor modules are missing in  cpufreq's package.
• Powernowd doesn't load on startup, but it does work manually. Probably something is messed up with the startup script. 

Thank you,

---

### Post by calmo on 2009-11-15
I'm having the same problem with 9.10 on a Thinkpad T43p.  Min and max settings for cpufreq are both set to 800Mhz...

[INDENT][FONT=Courier New]# cpufreq-info 
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 2.13 GHz
  available frequency steps: 2.13 GHz, 1.87 GHz, 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  **current policy: frequency should be within 800 MHz and 800 MHz**.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.13 GHz:0.00%, 1.87 GHz:0.00%, 1.60 GHz:0.00%, 1.33 GHz:0.00%, 1.07 GHz:0.00%, 800 MHz:0.00%  (78)
[/FONT][/INDENT]Doing this doesn't change anything:
[INDENT][FONT=Courier New]echo 2133000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq[/FONT]
[/INDENT]

---

### Post by wahlau on 2009-11-23
i have the same problem too since i upgrade to 9.10. No matter what i try, my cpu freq stays at 800Mhz. A reboot will allow me to use it at 1.87 when full load for a while, but at random time it would change to 800Mhz and cannot be changed anymore.

hope someone can help...

---

### Post by hwttdz on 2009-11-23
Users meet launchpad [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

