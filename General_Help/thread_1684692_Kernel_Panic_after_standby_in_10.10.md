---
title: "Kernel Panic after standby in 10.10"
date: 2011-02-09
forum: General Help
---

### Post by jrile on 2011-02-09
Hey guys, after days of searching for a way to fix this problem I still have not come up with a solution. I have a Toshiba Satellite laptop, dual-boot with Win7 and Ubuntu 10.10.  Everything works as it should in Ubuntu, except when I resume from standby the computer goes into a "kernel panic," the screen freezes and caps lock light blinks.

I travel with my laptop and use standby all the time being a student, so I've been forced to use Windows 7 because it's far more reliable (isn't that funny >_<) when I resume from standby..

After literally searching for DAYS, no solutions have worked for me, and apparently this is a pretty big issue. I would love to get Ubuntu running full-time on my laptop, so any help would be much appreciated! Also, my display drivers aren't officially supported by Ubuntu, but I'm not sure if that has anything to do with it.

Thanks!

---

### Post by ajgreeny on 2011-02-09
> Also, my display drivers aren't officially supported by Ubuntu, but I'm not sure if that has anything to do with it.What do you mean by that, exactly?

---

### Post by jrile on 2011-02-09
> **ajgreeny said:**
> What do you mean by that, exactly?

Sorry, I'm still a noob to the scene.
But when I went to get drivers for my monitor, Ubuntu said they were close-sourced and therefore not supported officially by Ubuntu or something like that.

---

### Post by ajgreeny on 2011-02-09
So did they come from the OS telling you that there are some additional drivers available for your hardware?  If so , they should be fine.

However, what graphics card do you have and what driver are you using?

---

### Post by jrile on 2011-02-09
> **ajgreeny said:**
> So did they come from the OS telling you that there are some additional drivers available for your hardware?  If so , they should be fine.

However, what graphics card do you have and what driver are you using?

Alright, I just booted up Ubuntu and here's exactly what it says when I go into the driver area:
"Proprietary drivers are being used to make this computer work properly. Proprietary drivers do not have public source code that Ubuntu developers are free to modify..." etc, etc.

It's the "ATI/AMD proprietary FGLRX graphics driver." Like I said, I have no idea if that's what's causing it. >_< 

Thanks for the quick replies!

---

### Post by jrile on 2011-02-09
Also, it appears to only happen when I'm running on battery power..

---

### Post by jrile on 2011-02-10
Well, I downgraded to 10.04 64 bit and it's working fine. I don't know if it's the 10.04 that helped, or the 64 bit.

---

