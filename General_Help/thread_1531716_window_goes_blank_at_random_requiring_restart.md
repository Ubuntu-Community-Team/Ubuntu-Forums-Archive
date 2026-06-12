---
title: "window goes blank at random requiring restart"
date: 2010-07-15
forum: General Help
---

### Post by jktjs on 2010-07-15
I have just installed kubuntu 10.04 (64 bit) on a moderately new Lenovo R500 laptop (dual-booting with Windows XP).

**Problem: several times per working day the screen goes blank.** It remains backlit, and I can still hear music or games if they were running beforehand. **The only way I have found out of the situation is a full restart**.

The problem occurs somewhat randomly, but is usually associated with movement of the mouse. Switching to a new user often causes the problem. Sometimes the screen freezes for 1 second before going blank. I have tried messing with the screensaver settings and the permissions for libusb (which are flagged in the mouse system settings page) without luck. 

Any help is appreciated!

---

### Post by Zorgoth on 2010-07-15
What is your graphics card and are you using compositing?

---

### Post by jktjs on 2010-07-16
Thanks for the help!

Graphics card: command "lspci | grep VGA" gives this line:
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

Compositing: I have disabled desktop effects because I don't want to spend CPU time on them.

---

### Post by Zorgoth on 2010-07-16
It may be a graphics issue or something else; I don't know.  Older ATI cards certainly have problems.  I would certainly test both the free and the proprietary graphics drivers to see if either of them fixes the problem (to switch between them in Ubuntu I believe all you need to do is activate/remove the entry in System>Administration>Hardware Drivers).

---

### Post by jktjs on 2010-07-16
Thanks for the idea.

I did Application Launcher > system > Hardware Drivers. I dowloaded and installed an ATI/AMD proprietary FGLRX graphics driver (the option suggested by the Hardware Drivers dialogue) and rebooted for the changes to take effect.

So far so good..... I will re-post in a few days to let you know whether this worked.

Cheers!

---

### Post by jktjs on 2010-07-27
Success!

It's now been about 10 days since I installed the proprietary graphics driver, and the screen-bank problem has not occurred again. My ubuntu installation is now working well.

I'm grateful for the help.

---

### Post by hornetster on 2010-07-28
Damn! And I thought that this might be similar to my problem.... :(
Installed Kubuntu 10.04 x86 yesterday, on some 'oldish' (D510 Ultra-slim Desktop) HP hardware, using intel 845g graphics, and doing the same thing. Thought it MAY be something to do with the powersaving, and have disabled any sleep/hibernate, but haven't had a chance to test properly since.
 John.

---

