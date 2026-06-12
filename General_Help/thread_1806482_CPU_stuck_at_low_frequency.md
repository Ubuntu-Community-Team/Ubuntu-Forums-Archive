---
title: "CPU stuck at low frequency"
date: 2011-07-17
forum: General Help
---

### Post by janerikm on 2011-07-17
On a freshly installed Dell Latitude D600 with Ubuntu 11.04 (Gnome) and all updates the laptop is running at a low frequency.

At startup the laptop runs at 1.7GHz, but when it's ready to use it's stuck at 600 MHz.

The governor used is ondemand. If I change this nothing happens and after a restart it is back with ondemand.

When I run 
cpufreq-set -g ondemand -u 1700000
I get no error but, but nothing happens.

Output from cpufreq-info:

[INDENT]eva@eva-Latitude-D600:~$ cpufreq-info 
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 600 MHz - 1.70 GHz
  available frequency steps: 1.70 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 600 MHz and 600 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz.
  cpufreq stats: 1.70 GHz:1.21%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:0.00%, 800 MHz:0.00%, 600 MHz:98.79%  (1)

[/INDENT]Running at 600Mhz the laptop is just to slow to use even for my mother (who is the owner who complained of a slow 10.10, which I tried to upgrade to 11.04 but failed and then did a clean install).

Disabling Speedstep in Bios is not an option since doing that sets the CPU speed at 600 MHz to "protect" the computer.

What can I do to get the CPU frequency control work in Ubuntu and avoid installing Windoze for her again?

---

