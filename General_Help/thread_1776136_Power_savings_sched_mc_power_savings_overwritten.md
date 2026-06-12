---
title: "Power savings: sched_mc_power_savings overwritten"
date: 2011-06-05
forum: General Help
---

### Post by belltown on 2011-06-05
I've been experimenting with some power-saving tweaks. One of them involves setting sched_mc_power_savings to "1" to utilize one cpu core fully and keep the others idle for longer.

I've put the following in /etc/rc.local

```

cat /sys/devices/system/cpu/sched_mc_power_savings >> ~john/junklog
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
cat /sys/devices/system/cpu/sched_mc_power_savings >> ~john/junklog

```I've verified that before the echo command, sched_mc_power_savings is set to "0", and after the echo command it gets set to "1". However, after the system finishes booting, the value is set back to "0" again.

Something is overwriting the value after I have set in in rc.local. Any ideas?

---

### Post by micaeked on 2011-06-08
i had a similar problem (contents of rc.local did not seem to take effect). to fix, i added "sleep 20" before any of my own commands

---

