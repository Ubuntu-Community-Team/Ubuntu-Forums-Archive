---
title: "Random Freezes (Last few days)"
date: 2006-05-06
forum: General Help
---

### Post by Parksy on 2006-05-06
My computer has started freezing randomly.  It happens about once an hour now; when it happens, everything stops.  My music quits playing, X freezes, and I can't do anything with the mouse or keyboard.  All I can do is power down.  It's just started happening recently too.  If I remember correctly, it started after my last updates, which had a bunch of new Xorg packages.  I'm not sure about that though.  Has anyone else had this happen?

I've tried looking through the logs, but I can't find anything there. Is there a certain log file I should check, or something I can enable to get more verbose logging?  I have no idea what the problem is.

---

### Post by RedeyesUK on 2006-05-06
I don't know if this is the same thing, but my system has just started logging itself out when I leave it idle for more than a few minutes. It seems to be some kind of security feature, but it never used to do that!

Definately seems to have something to do with the updates, I was fine before this as well.

---

### Post by tseliot on 2006-05-06
[QUOTE=RedeyesUK]I don't know if this is the same thing, but my system has just started logging itself out when I leave it idle for more than a few minutes. It seems to be some kind of security feature, but it never used to do that!

Definately seems to have something to do with the updates, I was fine before this as well.[/QUOTE]
Reinstall the drivers for your graphic card, the xserver updates broke opengl. 

Explanation of your current problem:
When you leave your computer idle, your screensaver starts, tries to use opengl and (error) it goes back to the login screen.

---

### Post by RedeyesUK on 2006-05-06
Excellent, thanks for that, I'll give it a try. I was thinking along those lines, especially when I tried to access the screensaver control panel and got logged out as a result.

Sorry for the hijack, Parksy!

---

### Post by RedeyesUK on 2006-05-06
Excellent, thanks for that, I'll give it a try. I was thinking along those lines, especially when I tried to access the screensaver control panel and got logged out as a result.

Sorry for the hijack, Parksy!

---

### Post by Parksy on 2006-05-06
Good to see things are working for someone at least.

I've tried blacklisting my wireless card drivers (hostap...not using them anyways), but that hasn't helped.  Not too sure sure what else to try.

---

### Post by Parksy on 2006-05-06
I just got the idea that it might be a CPU temperature problem.  I can monitor the temperature by looking at /proc/acpi/thermal_zone/THM0/temperature...just after the last crash, the temperature was over 60 degrees.  Is there some way to control when the CPU fan turns on?  The computer is a thinkpad T23.

---

### Post by yetanothersteve on 2006-05-07
I had the same issue after I updated X on Breezy 5.10 when all the updates came down a few days ago. I would walk away from the PC and when I came back it was at the login screen. Guessed that it might be the screensaver starting and crashing X so I went into System -> Preferences -> Screensaver and the X Server crashed immediately. Found this thread and decided it was time to reinstall the NVidia drivers and grabbed the 1.0-8756 drivers from NVidia because I was feeling lucky.

I used tseliot's method number 2 from this thread and everything is working well again. 
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=method+nvidia]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=method+nvidia")

Good luck.

---

### Post by sabredog on 2006-05-10
I have the same issue, either freezing just after the desktop appears or when the screensaver is running and I need to type my password in to get back to the desktop.

Does anyone know what is causing the issue?

I will re-install the Nvidia drivers via Automatix, to see if that solves the issue in the meantime.

---

### Post by sabredog on 2006-05-11
Well that did fix it, but only after I set the default video drivers to "nv" by editing xorg.conf and then restarting the ssesion. 

This enabled me to re-install the Nvidia drivers via Arnieboy's most excellent Automatix. A reboot and et voila! Problem solved.

Lesson learned; ALWAYS reinstall Nvidia drivers after a kernel update!

---

### Post by philip13 on 2006-05-20
I have had the same problem and I believe I have tracked it down to malfunctioning acpi drivers.

Ubuntu loads all driver modules indiscriminately and in my case two incorrect acpi driver modules were live !
These were the pcc_acpi (panasonic acpi hardware) and sony_acpi modules.
So I removed them via modprobe -r and physically renamed the .ko module files
(located in /lib/modules/2.6.12-10-686/kernel/drivers/acpi  for 686 architecture)

Despite thrashing openGL my machine is still going fine !

Nvidia drive is the latest (8756) on a Pentium 4 with a GeForce 5700.

As an aside the freezing was not a full crash on my system, it cycled 4 minuets frozen / 40 seconds unfrozen !

---

### Post by Parksy on 2006-05-20
I changed my kernel a while back (moved to the 686 version) and I haven't hard problems with then.  I can't really figure out why the problem started, but it seems to be ok now.

With respect to driver loading, I had a similar problem with my network cards.  Both the orinoco and hostap modules would get loaded.  I disabled the orinoco modules by putting then in /etc/hotplug/blacklist.

---

