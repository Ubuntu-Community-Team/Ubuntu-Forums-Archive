---
title: "startup problem"
date: 2009-11-11
forum: General Help
---

### Post by fbeleznay on 2009-11-11
I am trying to turn on my son's (acer) laptop, and I cannot get Ubuntu running. It worked fine when he turned it off previously. I cannot even get it running in recovery mode. The message before it stops is the following:
 
mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_add_match_subsystem_devtype
init: mountall main process (753) terminated with status 127
[    6.000120] Clocksource tsc unstable (delta = -255258466 ns)
 
the system is Ubuntu 9.04
 
Can you suggest something to do? I am a beginner with Ubintu.
Thanks

---

### Post by TetonsGulf on 2009-11-11
From what I've seen on other threads, it looks like people are resorting to reinstalls for this type of problem... [http://ubuntuforums.org/showthread.php?t=1309423](http://ubuntuforums.org/showthread.php?t=1309423)

I really have no additional information, but I am replying because I want to see how this plays out.

A suggestion though: If you have the LiveCD or can download & burn 9.10, I suggest popping that in and using a USB drive to copy your sons docs, music, videos, etc. so they aren't lost. It would make a reinstall less painful if you don't lose everything.

I'll keep searching some other forums as well.

---

### Post by TetonsGulf on 2009-11-11
See if this gets you going:

[http://ubuntuforums.org/showthread.php?t=1302866](http://ubuntuforums.org/showthread.php?t=1302866)

---

### Post by fbeleznay on 2009-11-11
Thanks for the link. I try it tomorrow, when I can get hold of a live CD. I let you know what happened.

---

### Post by fbeleznay on 2009-11-12
I logged in with the live CD without problem, did what it said on the link to adjust the clock, but unfortunately it didn't work. I still have the same login error message. I guess it will be a reinstall. Thanks anyway.

---

### Post by kkady32 on 2009-11-18
i have the same messages:Clocksource tsc unstable (delta = -293719238 ns)

i find this in internet:

"TSC=Time Stamp Counter. Processors have dynamically changed clock speed (ofc to save power). The TSC is supposed to tick at the CPU rate (unless it's a constant_tsc, see /proc/cpuinfo flags, so on frequency change, this ought to happen. The kernel will automatically switch to something else. There's acpi_pm <-(this is what yours has switched to) and, IIRC, pit. This message seems to appear with the newer kernel upgrades."
Check you have installed another clock source like acpi_pm

cat /sys/devices/system/clocksource/clocksource0/available_clocksource

You can try adding the below to your kernel command line. This won't get rid of the unstable line but it will force the kernel to use a more stable clocksource so there should be no trouble switching over anymore (if indeed there is trouble to begin with).

clocksource=acpi_pm

I will make probe but in moment i must see how cann type this command for grub2.
Please the post the results.

I tried with acpi_pm and with hpet but and the results was i need more time to boot: Clocksource tsc unstable (delta = -101708686 ns)
So is better for me to not set clocksource

---

