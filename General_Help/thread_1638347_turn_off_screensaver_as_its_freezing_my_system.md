---
title: "turn off screensaver as its freezing my system"
date: 2010-12-05
forum: General Help
---

### Post by inearlygaveup on 2010-12-05
Xubuntu 10.10

I need to turn off my screensaver as its freezing my system when it activates.
I have tried to go into > settings > screensaver but it locks my system up as soon as the screensaver options page comes into view.

I don’t really need a screensaver so is there any way to turn it off via the terminal or any other method.

Any suggestions please

---

### Post by 4Orbs on 2010-12-05
From the main menu, open the XFCE Settings Mgr. Then choose the "Sessions and Startup" settings, go to the Autostart Applications section. Remove the checkmark next to "Xscreensaver" and close the settings mgr. Reboot, and the screensaver should not try to kick in anymore.

Another option is to activate the proprietary driver for your video card, then the screensaver should work without freezing your machine. To activate the driver, go to the main menu "System">"Additional Drivers" and choose to activate the recommended driver. Reboot when prompted. If this works, but you still don't want the screensaver... open the screensaver settings and choose the option to either "Blank Screen Only" or "Disable".

---

### Post by inearlygaveup on 2010-12-07
Thanks 4Orbs 

Unfortunately there is no Xscreensaver entry in >XFCE Settings Mgr > Sessions and Startup > Autostart Applications.

I also don't have any "Additional Drivers" listed.

I think the problem is the old pc that it's on, it only has 256mb of ram.

When I open the screensaver options page the random theme is selected (must be by default) and I think it just overloads the system.

Trouble is I can't get in to switch the screensaver off completely.

---

### Post by azertyh on 2010-12-07
hello,
uninstall xscreensaver from synaptic if you don't need it.

---

