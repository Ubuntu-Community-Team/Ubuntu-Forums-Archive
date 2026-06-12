---
title: "CPU Speed Showing less than BIOS"
date: 2009-09-18
forum: General Help
---

### Post by fogNL on 2009-09-18
I have a Core i7 920 CPU that I have overclocked to 3.6GHz, which shows up fine in the BIOS and in Windows 7.

After installing Ubuntu 9.04 x64, I noticed that it was scaling the CPU back to 1.6GHz (even when trying to tax the cpu, it would only scale up as far as 2.6).  So, I went ahead and stopped the OnDemand service, and tried to change my governor from ondemand to Performance using cpufreq-selector on each core.  However, the max it will go up to is 2.6GHz.

I tried with the Gnome applet to select the CPU speed and it only ranges from 1.6GHz up to 2.6GHz.  Even without overclocking, my CPU speed should be at least 2.8GHz (133QPI x 20 (+1 turbo) multiplier).

What would be causing this?

---

### Post by XCan on 2009-09-18
I'm currently on a Q9450, and I've yet to find a hardware monitor that shows the true speed of my overclocked CPU, or FSB for that matter. I believe the monitors in Ubuntu are simply reading off the factory numbers from the chip. If you have overclocked it in BIOS, then it's set, no matter what Ubuntu or any other OS thinks it is. A simple test, run super_pi or something in stock and OC, and you should see the difference. I definitely do.

---

### Post by fogNL on 2009-09-19
Ok, as it turns out, /proc/cpuinfo does not display the correct speed.  The only way I can get the actual correct current speed is:

sudo dmidecode | grep -m1 "Current Speed"

This gives me my correct CPU speed of 3620MHz

---

### Post by earthpigg on 2009-09-19
hi,

i am pretty sure 9.04 low-level support for i7 ain't to hot yet.

for example, lm-sensors in ubuntu 9.04 was pretty useless. i think it detected ***one*** thing on my motherboard, and iirc it was something useless like the speed of ***one*** of my fans.

so, i went ahead and installed Arch. very good chance i will go back to Ubuntu once their support is up to par.

and, cpu config tools work better.

example:

```
analyzing CPU 4:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 4
  hardware limits: 1.60 GHz - 2.67 GHz
  available frequency steps: 2.67 GHz, 2.67 GHz, 2.53 GHz, 2.40 GHz, 2.27 GHz, 2.13 GHz, 2.00 GHz, 1.87 GHz, 1.73 GHz, 1.60 GHz
  available cpufreq governors: powersave, ondemand, performance
  current policy: frequency should be within 1.60 GHz and 2.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.
```

1.6 is exactly where i want my 2.67 Ghz quad core right now. i am able to control this in arch.

this was not the case with 9.04.

i have heard 9.10 Alpha improves this vastly.

_**if i where you and wanted low level control over this type of stuff:**_
-wait.
-consider Ubuntu 9.10 Alpha.
-consider any [rolling release]("http://en.wikipedia.org/wiki/Rolling_release") distribution. (i picked Arch over 9.10 Alpha to see WTF the big deal with Arch was. aside from better hardware support and the forced-learning, i am not especially impressed.)

---

### Post by 98cwitr on 2009-10-01
I was a little baffled myself when it was only listing 2400Mhz for my oc'd e6750 (stock 2.66, right now @ 3.20)

sudo dmidecode | grep -m1 "Current Speed"

worked...thanks.

---

### Post by egalvan on 2009-10-01
> **cquilliam said:**
> Ok, as it turns out, /proc/cpuinfo does not display the correct speed.  The only way I can get the actual correct current speed is:

sudo dmidecode | grep -m1 "Current Speed"

This gives me my correct CPU speed of 3620MHz

Yep, this works a charm.

Many Thanks!

---

### Post by r3aktor.mkd on 2009-10-01
Hello,
I have Q6600 @ 2,4 GHz.

The thing here is that when the PC is idle,
the processor automaticly enters in kind of energy save mode.
So, mine is working at 1,6 GHz in idle and 2,4 when processing.

---

