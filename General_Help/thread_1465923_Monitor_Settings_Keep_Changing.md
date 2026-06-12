---
title: "Monitor Settings Keep Changing"
date: 2010-04-29
forum: General Help
---

### Post by IMSargon on 2010-04-29
I have several computers attached to a KVM. One of these is a laptop which I recently upgraded (clean install) from 9.10 to 10.04. I have set this computer to turn off the laptop display and only to use my attached monitor. I had no problems doing this under 9.10. Now, after several minutes of using one of the other computers, the Ubuntu 10.04 computer will reset its own monitor settings such that the external monitor is disabled and it turns on the laptop monitor again. How do I disable this new "feature"?

---

### Post by IMSargon on 2010-05-03
I am still having this issue. I just need to know why the screen settings change automatically when they did not in the previous version of Ubuntu.

---

### Post by marvelty on 2010-05-04
I also have this problem, though I am  simply plugging in the external monitor to my 
laptop.  It seems every time it goes to screensaver it loses the monitor settings and defaults to a dual-screen setup. It also loses any changes to relative orientation (laptop below external vs. beside) at the same time. 

I have not found a solution. Anyone else out there have any insight?

---

### Post by IMSargon on 2010-05-05
@marvelty

Yes, this is the same problem for you, but I think I know a workaround for your particular case.

What I think is happening is that after switching to your screensaver, your monitor goes into sleep mode. The computer detects this as a disconnect (just as my KVM causes a disconnect) and automatically creates new monitor settings. When you use your computer again, the monitor wakes up, the computer detects the "new" monitor, and sets some default dual-monitor settings.

To work around this, you could go to your power settings and tell the monitor not to use sleep mode (Preferences -> Power Management Preferences). Of course, now you're wasting energy and wearing out your LCD backlight for nothing, so it's not an idea solution. We're still waiting for someone to tell us how to disable this new monitor auto-configuration "feature".

---

### Post by huepfend_schof on 2010-05-20
I have the same problem, but your workaround is not always working.
I have an external monitor attached to my laptop through a docking station. I want the laptop monitor to be switched off. But sometimes, after a reboot, the Ubuntu lucid is switching the laptop monitor on again. This is annoying, because, then the panel is on the screen of the closed laptop. In Ubuntu karmic, I had no problems.
Does a bugreport is existing for this problem, I found none.

---

### Post by IMSargon on 2010-06-05
Yeah, my workaround won't survive a reboot, it only helps in the limited case of a monitor going to sleep. I'm still waiting for a knight in shining XOrg expertise to come and rescue us... 

Someone? Anyone?

---

### Post by wojox on 2010-06-05
What Graphics card/chip you running?

---

### Post by IMSargon on 2010-06-05
In my case, this is an ATI Mobility Radeon 9700.

---

### Post by noleks on 2010-06-07
I think I may have a "related" issue.  I have an Ubunti 9.1 box hooked up to a monitor through a KVM switch.  It seems to be unable to detect the monitor through the KVM switch on boot/reboot so it appears to be autoconfiguring to 640x480, which is really annoying.
If I connect the monitor directly to the Linux box and boot, it appears to properly detect and use the optimal settings.
Does anyone know how to "lock" the configuration, or maybe skip a monitor autodetect step on boot?

---

### Post by PaganBlasphemy on 2010-06-07
Another laptop user with an external monitor reporting in with the same problem (monitor configuration gets reset on suspend/sleep) in Ubuntu 10.04

---

