---
title: "CPU at 100%, scaling disabled, oh my!"
date: 2009-08-25
forum: General Help
---

### Post by yoman82 on 2009-08-25
I have an Athalon X3, the one with the extra core. I had it on on demand CPU scaling (With all 4 cores enabled). One day, I decided to overclock it 5%, using my MB's built in overclocking. It booted normally into Ubuntu, but I got a message saying frequency scaling was not enabled. Whatever, to be expected, right? I turned off the scaling applet. However, I noticed my computer was running hot, so I shut down and disabled the increase in clock speed, then the manager in BIOS. When I booted back in, scaling was STILL disabled, and I have 100% CPU usage on all of my processors the computer is running hot, at 130ish. Help would be greatly appreciated.

---

### Post by yoman82 on 2009-08-25
I fixed the mad CPU usage, I had a rogue daemon, now what about the scaling?

---

### Post by tgeer43 on 2009-08-25
First make sure that if there are any settings in your BIOS pertaining to frequency scaling that they are set correctly. Then try entering the following lines in the terminal:
```
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
```to see if it gives any errors and whether frequency scaling is now set to 'on demand'.

tgeer

---

