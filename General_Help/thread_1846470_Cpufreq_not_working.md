---
title: "Cpufreq not working"
date: 2011-09-19
forum: General Help
---

### Post by Neodarkness on 2011-09-19
Hello guys.
I recently borked my ubuntu 11.04 install accidentally. I´m trying to install it again, but my laptop overheats in the livecd. I can´t seem to find a way to change my cpu from running at full 1.9 
(performance) speed to 0.8 (ondemand)... I know it´s possible, since last time I managed to do it, but I can´t remember what the trick was.
I installed cpufrequtils and modprobed powernow-k8 and cpufreq_ondemand and then tried doing cpufreq-set -g ondemand, but it fails to change the governor.
Furthermore, /sys/jdshjlhdsl/cpu/cpu0/cpufreq/ does not exist!
I´m clueless and already tried 11.04 and 11.10 but to no avail.
I really really need my laptop to work on the ondemand governor as it overheats and shuts down otherwise.
Could someone be kind enough to help me out getting that working?
All help is very appreciated, but please dont go second-guessing my needs... I know I should clean my fans, update my bios and/or buy a new laptop, but thats not what I MUST do right now. I just need Cpufreq to set on ondemand :s

EDIT:

I managed to fix the problem by myself. I'm leaving the fix here in case someone may find it useful.
In order for you to make cpufreq modules to load correctly you have to pass the kernel parameter "acpi=force" on boot (the option is not explicitly available on 11.10, but you can write it yourself). After doing that I enabled universe and installed cpufrequtils and it loaded automatically the appropriate modules all by itself.
Hope this helps someone :)

---

