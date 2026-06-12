---
title: "Dual Monitor Issues with fglrx"
date: 2009-07-08
forum: General Help
---

### Post by lunarmelody on 2009-07-08
Hello all,
I've been trying to get fglrx working on my machine.  I'm running Ubuntu 9.04 with a ATI Radeon HD4670 graphics card.  I've downloaded the driver file ati-driver-installer-9-6-x86.x86_64.run and gotten it to install, and I've been able to adjust the screen resolution using the Catalyst Control Center successfully with one monitor connected.

The problem I'm having occurs when I try to enable my second monitor.  The second monitor will display the desktop, but periodically it will flicker, and when it does so it blocks all input/output (i.e., I can't do anything until the flickering stops, even on my main monitor).  

It also won't allow me to drag windows onto my second monitor.  I tried enabling Xinerama through the Catalyst Control Center, which looked like it would enable span, but that made things worse.  After enabling Xinerama, I restarted my machine (as asked to), but then it just booted to a black screen instead of showing me the login screen.  I had to reboot my machine into a root shell using the recovery mode and remove the driver from there to get it to boot.

Is there anything I can do to fix this, or is it a lost cause?  Thank you in advance for any help.

---

### Post by lunarmelody on 2009-07-17
I managed to get these problems fixed by adding ```
Option "EnableRandR12" "false"
``` to the Device section of my xorg.conf file.  Apparently xinerama is not compatible with RandR 1.2.  I have a few more questions though.

I've been playing around with the desktop effects to see if I could get them to work with no success.  Enabling them through the Appearances dialog gives me the error "The Composite extension is not available", while the compiz_check script returns that I am not using a rendering method (Rendering method:  None).  I saw somewhere on the forums that to fix this, you need to add ```
Option "AIGLX" "on"
``` to the ServerLayout section of xorg.conf.  This has not worked for me.  Is there any way to fix this?

Also, I've noticed that I apparently have one mouse cursor for each monitor.  When I move from monitor 1 to monitor two, a mouse cursor remains on the right side of monitor 1, while a different mouse cursor appears on monitor 2.  Same thing happens if I go back; a mouse cursor stays on the left side of monitor 2, while the mouse cursor that remained on monitor 1 reacts to my mouse again.  This isn't a problem, instead being merely annoying, but does anyone know of a fix to this? 

Thank you in advance.

---

### Post by lunarmelody on 2009-07-27
*bump*  Anyone have any ideas?

---

### Post by CycleLock on 2009-07-31
Found this while looking for a solution to the same problem.

[http://ubuntuforums.org/showthread.php?t=1174943&highlight=screen+flicker&page=3](http://ubuntuforums.org/showthread.php?t=1174943&highlight=screen+flicker&page=3)

---

