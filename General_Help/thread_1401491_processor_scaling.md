---
title: "processor scaling"
date: 2010-02-08
forum: General Help
---

### Post by gabrielcik on 2010-02-08
Hello,

Can you pls say me in what way i can set the processor scaling to switch automatically on performance while the pc is connected to the AC.

Thank you

---

### Post by Baneblade on 2010-02-08
That should be complete automated. You shouldn't have to do anything.

---

### Post by shriramrs31 on 2010-02-08
It is by default on demand. executing the following command as root

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

gives you supported frequencies by your processor. So according to your usage ubuntu automatically upscales / downscales it. There actually is no use to spike it up when the system is not running any CPU intensive programs ;-) and when something heavy comes up, the OS automatically switches it to the max frequency.

If you sill want manuall control, you can install the CPUFreq monitor applet for each CPU by right clicking panel and then manually selecting what frequency you want.

I am pretty sure since jaunty this applet saves the previous selected value after reboot, but you should try it out.

---

### Post by onamattuphere on 2010-02-08
Hi. I just worked my way through a similar problem. If you're having a hard time figuring it out, have a look at [my freshly solved thread]("http://ubuntuforums.org/showpost.php?p=8693968&postcount=9").

Good luck

---

### Post by gabrielcik on 2010-02-08
Hello,

The situation is the following:

When connected to AC at the startup is on performance then suddenly few seconds later it switch to on demand.

---

