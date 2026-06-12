---
title: "Machine is borked"
date: 2010-06-14
forum: General Help
---

### Post by AstroLlama on 2010-06-14
Today, bringing my laptop out of sleep the fan started spinning, but never stopped. The hard drives made regular noises coming out of sleep, but the fans continued spinning and the screen remained dark. Completely unresponsive, after trying REISUB (to no success) I did a hard shutdown with the power button.

I thought this was inconvenient, but not serious, as similar things have happened in the past (but not recently, Ubuntu is much more stable than it was years ago) and rebooting always made it go away. This time, however, when I boot the machine the fan spins, the drives make regular noises, but the screen stays black. 

This is very inopportune, as Wednesday I am leaving the country and will need my computer for work. Does anyone have an idea of what might be causing this problem? Could this be related to a botched security update? I referenced the interwebs but couldn't find a solution. FYI, I haven't tinkered with anything in the OS. This happened after a clean install of 10.04 a month ago (and some standard installs from the "software center" menu)-- but no CLI tinkering!

---

### Post by CharlesA on 2010-06-14
Are you able to boot off a liveCD?

It sounds like a hardware probably tbh, but Ubuntu has always had problems with suspend/hibernate, so I wouldn't rule that out.

---

### Post by 5BallJuggler on 2010-06-14
I had something similar with my Acer Aspire One,

It was down to a Bios Issue, I got a new configuration file from Acer and re-flashed my system, after reboot everything was fine.

---

### Post by AstroLlama on 2010-06-14
No Live CD boot, though I discovered that the computer isn't 100% unresponsive. if I press alt+f1 (which makes it go to sleep) the machine turns the fan off and goes into sleep mode. starting it again doesn't make a difference. I plugged an external monitor in, thinking it could be a display issue, but still didn't get any picture. I can't even access the BIOS! (or if I can i can't tell because the screen remains dark)

---

### Post by 5BallJuggler on 2010-06-14
Can you take the HDD out and place in another laptop/desktop, that is how I figured that my data was OK, and it was an issue with the hardware.

---

### Post by AstroLlama on 2010-06-14
> **5BallJuggler said:**
> Can you take the HDD out and place in another laptop/desktop, that is how I figured that my data was OK, and it was an issue with the hardware.

I don't have too much experience doing that, so that will have to wait until at least tomorrow or later this afternoon. I really hope it's not a hardware issue!

---

### Post by GabeSmall on 2010-06-14
Don't know if this will apply to your situation, but I had a similar problem after selecting Hibernate rather than Shutdown from the power menu. I was able to get to the boot loader only after powering down, disconnecting the power, and removing the battery. (I also waited fifteen minutes for good measure.) Once I got to the boot loader, I followed the instructions here:
[http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html](http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html)

To avoid this happening again, I found a solution in these forums to disable Suspend and Hibernate:
[http://ubuntuforums.org/showthread.php?t=1477500](http://ubuntuforums.org/showthread.php?t=1477500)

---

### Post by jwbrase on 2010-06-14
> **AstroLlama said:**
> I don't have too much experience doing that, so that will have to wait until at least tomorrow or later this afternoon. I really hope it's not a hardware issue!

If it won't boot from a live CD, and you can't even access BIOS, it's a hardware or firmware issue. I suppose it could be something that the software did to damage the hardware or firmware, but that's rather unlikely.

---

### Post by GabeSmall on 2010-06-14
> **jwbrase said:**
> If it won't boot from a live CD, and you can't even access BIOS, it's a hardware or firmware issue. I suppose it could be something that the software did to damage the hardware or firmware, but that's rather unlikely.

I'm not so sure. It sounds eerily familiar to what I went through.

Try simply removing the battery before doing anything drastic.

---

### Post by GabeSmall on 2010-06-14
> **GabeSmall said:**
> Once I got to the boot loader, I followed the instructions here:
[http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html](http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html)

Forgot to mention:

When I followed these instructions, I did not see a line that starts with "kernel" (as per Step 3) but there was one that ended with "quiet" and "splash", which was the one I edited, and it worked as described.

---

### Post by AstroLlama on 2010-06-14
Update: I burned a new live CD and have been trying to get it to boot. The screen has not changed at all-- no blinking cursors, prompts, or illumination. External monitors will not work, and booting into grub or the bios is not working. When the boot CD is in the drive and the power goes on it sounds like it gets mounted, but there is no way to get around the screen that doesn't work. I feel like I'm driving a car without a steering wheel. I'll try to swap the hard drive and see where that takes me. I'm getting desperate!

---

