---
title: "Core unlocking and overclocking programs?"
date: 2011-12-28
forum: General Help
---

### Post by onipar on 2011-12-28
Sorry if this is the wrong thread...

I am planning to unlock cores and overclock on my new PC build, but most of the programs that people have suggested I use for temp control and stress testing were Windows based.

Can you recommend any programs for Linux/Ubuntu that I can use for stress testing, temperature monitoring/etc?

My system has an AMD Phenom II X3 and Gigabyte 880gma, with 8GB GSkills Ram.

Thanks!

---

### Post by Bobhuber on 2011-12-28
> **onipar said:**
> Sorry if this is the wrong thread...

I am planning to unlock cores and overclock on my new PC build, but most of the programs that people have suggested I use for temp control and stress testing were Windows based.

Can you recommend any programs for Linux/Ubuntu that I can use for stress testing, temperature monitoring/etc?

My system has an AMD Phenom II X3 and Gigabyte 880gma, with 8GB GSkills Ram.

Thanks!
lm-sensors
screenlets & screenlets-pack-basic

lm-sensors is the hardware monitoring module used by many programs in ubuntu and screenlets has several  apps  that create desktop widgets for system monitoring.

---

### Post by onipar on 2011-12-28
Thanks!  Is this something I just search in the software manager and download from there?

---

### Post by Irony on 2011-12-28
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

[IMG]http://i40.tinypic.com/15xsj1f.jpg[/IMG]

---

### Post by Bobhuber on 2011-12-28
> **onipar said:**
> Thanks!  Is this something I just search in the software manager and download from there?
That or the synaptic package manager that can be installed thru the software center

---

### Post by Frogs Hair on 2011-12-28
This maybe worth looking into . [http://amdath800.dyndns.org/amd/](http://amdath800.dyndns.org/amd/)

---

### Post by onipar on 2011-12-28
Thanks everybody.  I did the LM-sensor detect thing.  It seemed to work.  I'm now running Xsensor while I stress test, but it is only detecting 3 of the 4 cores (could this be because I did the "sensor detect" before I unlocked the fourth core?).

Also, I've never done this before, so I don't know what a normal temp reading looks like, but for the three cores, it ranges in temps from 12 C to 41 C.  The third is something like 31 C.  Does this sound normal?  I'm just not sure if the temp readings are accurate.

Thanks again.

---

### Post by Bobhuber on 2011-12-28
> **onipar said:**
>  but it is only detecting 3 of the 4 cores (could this be because I did the "sensor detect" before I unlocked the fourth core?).

Thanks again.
AMD Phenom II X3  >  4 cores ?????

Idle 30C
Load  (AMD Site) 73C

---

### Post by onipar on 2011-12-28
> **Bobhuber said:**
> AMD Phenom II X3  >  4 cores ?????

?

Not sure I understand what you're asking...

I unlocked the fourth core on my Phenom II X3 and my temperature monitor was only giving me temp readings for 3 of them.  SO I was asking why that might be.

I also asked on another forum and was told the reason for this is that when you unlock the fourth core on the Phenom II X3, the temperature readings stop working.  So that explains why I am only getting three core readings, and why they are "off" (giving the wrong temp readings, such as 12 degrees C).

SO pretty much it seems I'll have to watch the motherboard temp and subtract around 10 degrees C for an estimate of the CPU temp, since the CPU temp sensors are disabled.

No biggie really because I'm not planning on over-doing it with the overclock.  I'll probably only shoot for 3.2 Ghz, since I'm not gaming with this machine or anything.

Anyway, thanks all.

---

### Post by Bobhuber on 2011-12-29
> **onipar said:**
> ?

Not sure I understand what you're asking...

I unlocked the fourth core on my Phenom II X3 and my temperature monitor was only giving me temp readings for 3 of them.  SO I was asking why that might be.


Anyway, thanks all.
The reason I'm asking about 4/cores on the Phenom II X3 is that even with ACC set to auto in the bios you may or may not get the fourth core depending on the chip,MB and bios version.. Open system monitor and under the system heading how many cores do you see ? Are you running dual boot and able to see the 4/th core under windows? You can edit the /etc/sensors3.conf file to adjust temps for your cpu. Info found here.
[http://www.lm-sensors.org/wiki/Configurations](http://www.lm-sensors.org/wiki/Configurations)

---

### Post by onipar on 2011-12-29
> **Bobhuber said:**
> The reason I'm asking about 4/cores on the Phenom II X3 is that even with ACC set to auto in the bios you may or may not get the fourth core depending on the chip,MB and bios version.. Open system monitor and under the system heading how many cores do you see ? Are you running dual boot and able to see the 4/th core under windows? You can edit the /etc/sensors3.conf file to adjust temps for your cpu. Info found here.
[http://www.lm-sensors.org/wiki/Configurations](http://www.lm-sensors.org/wiki/Configurations)


Oh, I gotcha.  Yes, I definitely unlocked the forth core.  I checked in "system info," "system monitor," and an extra downloaded "Sysinfo."  They all now show my processor as a AMD Phenom(tm) II X4 20 instead of a AMD Phenom(tm) II X3  720, and in the monitors it shows four working cores.  Not to mention when I run Prime95 it detects 4 threads to test.

It's only the temp sensor that doesn't show 4 cores.  I was told this is because when you unlock the fourth core, the temp sensors don't work properly anymore.  I'll give that page you posted a look and see if I can get it working though.  Never hurts to try.

Oh, and no, I'm not running a dual boot.  Just Ubuntu.

Thanks for the suggestion, I'll give that a shot.  :D

Edit:  my motherboard model isn't on the list on that page you provided.  (Gigabyte 880gma-usb3)

---

### Post by onipar on 2011-12-29
I checked the temp (in the bios) before overclocking.  It showed system -> 28 C, and Core -> 27 C.

Interestingly, when I opened the xsensor program on the desktop, it  showed "temp 1" -> 28 C and "Temp 2" -> 27 C.  Temp 3 still reads as  the improbable 12 C, so I know that one isn't working.  But I'm  thinking those first two temps might be accurate.

My plan is to restart after the stress test runs a while, note those 2  temps, then check the temps in the bios again to see if they are still  matching up.  If so, I think those two are working...

---

### Post by xrhstaras on 2012-12-24
Warning !! Unlocking cores on amd phenom II 3+ghz from dualcore to quadcore + Using cpufreqindicator to set the cpu governor to performance will result to a completely unstable system.
You system will freeze for example while watching tv or converting media files etc.

I recomment you not use core unlocking on linux !

---

