---
title: "Can not set &quot;ondemand&quot; governer to scale frequency on Intel Atom D525 (oneiric amd64)"
date: 2011-11-01
forum: General Help
---

### Post by couling on 2011-11-01
Hi All

I'm trying to set CPU scaling on my low power server 
(Intel Atom D525 Running Ubuntu Server oneiric 11.10 amd64).

I've installed the package cpufrequtils.  I've tried setting the govoner to both conservative and ondemand.  But setting it to anything other than "Powersave" results in it being set to "Performance".

Digging into the kern.log, this leaves entries of the form:
```
Nov  1 15:39:33 zbox kernel: [  577.875645] conservative governor failed, too long transition latency of HW, fallback to performance governor
```Also I note the following:
```

cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_transition_latency
10000001
```This appears to be the same as this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706).
Only this bug appears to be resolved in a version significantly prior to 11.10 

Any suggestions?

---

