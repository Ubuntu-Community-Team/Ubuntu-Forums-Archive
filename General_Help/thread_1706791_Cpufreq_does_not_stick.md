---
title: "Cpufreq does not stick"
date: 2011-03-14
forum: General Help
---

### Post by mrwoody on 2011-03-14
Hi. 

I have been using kubuntu, and I would like to change the cpufreq settings. My understanding is that there is no applet for that, and I would have to do it by hands with a script. 

So I run a command like this: 

```

sudo cpufreq-set  -g userspace -c 0 -d 800Mhz -u 1200Mhz

```

and when I type cpufreq-info, I get
```

cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 1.20 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.
  cpufreq stats: 2.50 GHz:70.06%, 2.50 GHz:0.97%, 2.00 GHz:4.85%, 1.60 GHz:0.35%, 1.20 GHz:2.89%, 800 MHz:20.88%  (193873)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.00 GHz and 2.00 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
  cpufreq stats: 2.50 GHz:83.43%, 2.50 GHz:1.03%, 2.00 GHz:4.28%, 1.60 GHz:0.01%, 1.20 GHz:1.74%, 800 MHz:9.50%  (3208)

```

which shows that everything worked well (on cpu 0). 
The problem is that if I run cpufreq-info again after few minutes I get

```


cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.50 GHz:69.73%, 2.50 GHz:0.97%, 2.00 GHz:4.83%, 1.60 GHz:0.35%, 1.20 GHz:2.92%, 800 MHz:21.20%  (193880)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.50 GHz:82.94%, 2.50 GHz:1.03%, 2.00 GHz:4.33%, 1.60 GHz:0.01%, 1.20 GHz:1.73%, 800 MHz:9.96%  (3215)

```

so it looks like some other process changed the settings. Does anyone know how to fix this? 

**Thanks!**

**Edit:** I also tried many different settings, but I get similar behavior.

---

### Post by andrewthomas on 2011-03-14
> **mrwoody said:**
> 

```

sudo cpufreq-set  -g userspace -c 0 -d 800Mhz -u 1200Mhz

```and when I type cpufreq-info, I get
```

  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
    CPUs which need to have their frequency coordinated by software: 1

```
  
Try setting them both and see if it sticks then.
```

sudo cpufreq-set  -g userspace -c 0 -d 800Mhz -u 1200Mhz
sudo cpufreq-set  -g userspace -c 1 -d 800Mhz -u 1200Mhz

```

---

### Post by mrwoody on 2011-03-14
> **andrewthomas said:**
> Try setting them both and see if it sticks then.
```

sudo cpufreq-set  -g userspace -c 0 -d 800Mhz -u 1200Mhz
sudo cpufreq-set  -g userspace -c 1 -d 800Mhz -u 1200Mhz

```

Thanks for your help, but it doesn't seem to help. What I realized 
is that it would change mode only after I run something heavy (e.g. website with flash), the problem is that it wouldn't go back to a more economical mode after that process is over.

---

### Post by andrewthomas on 2011-03-15
It sounds like you should be using the ondemand scaler.

---

### Post by mrwoody on 2011-03-15
> **andrewthomas said:**
> It sounds like you should be using the ondemand scaler.

I tried that... same results.

---

