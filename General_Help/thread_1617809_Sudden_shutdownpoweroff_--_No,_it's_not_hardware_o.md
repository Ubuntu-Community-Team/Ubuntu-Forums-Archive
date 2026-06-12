---
title: "Sudden shutdown/poweroff -- No, it's not hardware or dirty fans"
date: 2010-11-09
forum: General Help
---

### Post by jrtayloriv on 2010-11-09
I just did a clean reinstall of Ubuntu (10.04 --> 10.10). After the install, any time I do CPU intensive work, my PC is suddenly shutting down like it's overheating.

**Everything was working fine for months, and started having problems immediately after the reinstall. so this is not a problem with my hardware, and it's not a problem with my fans needing cleaning -- it's a problem with software. So please don't tell me "that sounds like overheating, clean your fans".** Something is different in software-land between 10.04 and 10.10 that is causing this to happen -- I assure you that the upgrade did not magically fill my fans with cat hair.

I have checked my log files, and can't find anything related to overheating -- searches for things related to lm_sensors, "temp", and "thermal" are not turning up anything in the system logs (syslog, kern.log, or messages). I also looked at the logs around the times of the sudden shutdown, and couldn't find anything unusual. 

How can I diagnose this? I'd like to file a bug report, but since I can't find anything in the logs, I honestly have no idea how to go about providing useful information.

Is there anything besides overheating that might be causing my laptop to suddenly shut off?

Thanks,
Jesse

(I am using a Gateway M-6888u laptop, btw)

---

### Post by murrayju on 2010-11-24
I am having a similar issue. In my case, I have a system that has been running Windows 7 just fine for months. When I run the installer for Ubuntu Server 10.10 x64, I get to the stage where it says "Detecting Hardware" for a second, and then the PC just powers off. I have previously run 10.04 without any issues on this same setup, so I may have to go back to that for the time being. Have you found any workarounds yet?

---

### Post by trackisimo on 2010-12-17
Hello,

I also have problems of system suddenly shutting down.
I have ubuntu 10.10 and the sudden power off happened to me a few times in the last month since I installed 10.10 (clean install on my sony VAIO VGN-CS290).

I think it's something with the hardware because it happens when there is too much processing to do (especially I notice that it haapens when I go to webpages containing lots of flash content, but I can't be sure about it).

I'm not sure but I think I had tis behavior a few times with 10.04 installed (never saw it with windows 7), maybe something in the ubuntu OS cause the processor to go extra hot!

Anyway I'm going  to replace my laptop fan and will try to put arctic silver 5 on the cpu and heat sink to reduce the heating.

If you have anything new I'll be glad to know.

---

### Post by murrayju on 2010-12-17
The solution in my case was a new power supply. Didn't make sense because Windows 7 ran fine for months, but as soon as I popped in a new one, everything worked perfectly. The Linux install must do some hardware checks that draw more power than Windows ever was.

---

