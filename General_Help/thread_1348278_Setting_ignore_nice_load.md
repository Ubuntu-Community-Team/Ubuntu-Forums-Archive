---
title: "Setting ignore_nice_load"
date: 2009-12-07
forum: General Help
---

### Post by Otustelija on 2009-12-07
I'm trying to set /sys/devices/system/cpu/cpu*/cpufreq/ondemand/ignore_nice_load during the boot process to keep my CPU frequency down while running Folding@Home (origami). I tried putting echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load in my /etc/rc.local, but it does not have any effect. Maybe the value is reset afterwards?

Where should I put the statement to make the value stick?

---

### Post by Otustelija on 2009-12-09
I found the problem in [https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/344252](https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/344252)

The governor defaults to performance until 60 seconds after boot. The solution was to put the echo statement in /etc/init.d/ondemand and while at it I changed 60 to a more realistic 20.

---

