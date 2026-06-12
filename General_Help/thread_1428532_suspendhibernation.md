---
title: "suspend/hibernation"
date: 2010-03-12
forum: General Help
---

### Post by zcartist on 2010-03-12
I have a 9.10 install on an Aopen mini fanless system. Whenever I leave it the screensaver comes on. It goes into some kind of suspend/hibernation mode and I can't wake it up. I don't have sleep active in the settings.

---

### Post by spiderbatdad on 2010-03-12
it may be necessary to boot your computer with the kernel option acpi=off. You can try disabling the screensaver in sysytem>>preferences>>Screensaver and/or fiddling with power management...making sure each change to click "make default," but if this issue isnt resolvable then its acpi=off or a possibility of disabling the system apci in the bios.

---

### Post by zcartist on 2010-03-13
Thanks for the reply. The power management stuff has no effect. I can't seem to get in the bios. Any ideas?

---

### Post by efflandt on 2010-03-13
So in Power Management Preferences, On AC Power tab, do you have "Put computer to sleep when inative for: Never", and for Display, "Put display to sleep when inactive for: Never"?

And have you tried Blank Screen instead of a screensaver.  Some screen savers tend to lock up my computer.  I don't know if that is because my older Athlon64 lacks the lahf_lm instruction (I have to use flashplugin-lahf-fix to use 64-bit flash).

Otherwise you need to figure out how to get into CMOS setup at BIOS splash screen during boot, to check any power save settings in BIOS.  If your monitor does not wake up quick enough to see that, you may need to turn your monitor on before booting, instead of letting it wake up.

---

### Post by zcartist on 2010-03-13
I guess my only option is to leave the screen options off. The BIOS isn't F8 or F10 so I'm sort of stuck

---

### Post by zcartist on 2010-03-15
There is no off option for the acpi. Every option I try under that kills the power completely. The place I got it from has no fix either. They gave it to me free so I'm not complaining. Its hooked up to my hdtv so I can just switch inputs when idle

---

