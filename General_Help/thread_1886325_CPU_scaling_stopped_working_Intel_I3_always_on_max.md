---
title: "CPU scaling stopped working Intel I3 always on max"
date: 2011-11-24
forum: General Help
---

### Post by dakaku on 2011-11-24
I noticed today that my I3 always runs on max frequency.
Scaling used to work 2 days ago. I only installed eclipse c++/java and android sdk.
(Ubuntu 11.10).

cat /proc/cpuinfo |grep MHz
```
cpu MHz        : 2399.000
cpu MHz        : 2399.000
cpu MHz        : 2399.000
cpu MHz        : 2399.000

```I tried purge/install indicator-cpufreq/cpufrequtils/libcpufreq0

cpufreq-info:
```
driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3
  CPUs which need to have their frequency coordinated by software: 3
  maximum transition latency: 10.0 us.
  hardware limits: 933 MHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 2.27 GHz, 2.13 GHz, 2.00 GHz, 1.87 GHz, 1.73 GHz, 1.60 GHz, 1.47 GHz, 1.33 GHz, 1.20 GHz, 1.07 GHz, 933 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: _**f****requency should be within 2.40 GHz and 2.40 GHz.**_
                  The governor_** "performance" **_may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz.
  cpufreq stats: 2.40 GHz:98.21%, 2.27 GHz:0.00%, 2.13 GHz:0.00%, 2.00 GHz:0.00%, 1.87 GHz:1.77%, 1.73 GHz:0.00%, 1.60 GHz:0.00%, 1.47 GHz:0.00%, 1.33 GHz:0.00%, 1.20 GHz:0.00%, 1.07 GHz:0.00%, 933 MHz:0.02%  (21)

```After setting the governor to demand with: cpufreq-set -g ondemand -c0 / -c1 / -c2...
I get this with cpufreq-info:
```
driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3
  CPUs which need to have their frequency coordinated by software: 3
  maximum transition latency: 10.0 us.
  hardware limits: 933 MHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 2.27 GHz, 2.13 GHz, 2.00 GHz, 1.87 GHz, 1.73 GHz, 1.60 GHz, 1.47 GHz, 1.33 GHz, 1.20 GHz, 1.07 GHz, 933 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: **_frequency should be within 2.40 GHz and 2.40 GHz._**
                  The governor **_"ondemand"_** may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz.
  cpufreq stats: 2.40 GHz:98.55%, 2.27 GHz:0.00%, 2.13 GHz:0.00%, 2.00 GHz:0.00%, 1.87 GHz:1.43%, 1.73 GHz:0.00%, 1.60 GHz:0.00%, 1.47 GHz:0.00%, 1.33 GHz:0.00%, 1.20 GHz:0.00%, 1.07 GHz:0.00%, 933 MHz:0.01%  (21)

```

Edit:
Solved this myself by setting the min frequencies down to 0.933Ghz with:
sudo cpufreq-set -c0 -g ondemand -u 2.40Ghz -d 0.933Ghz
for each core, but im still curious why it got changed.

---

