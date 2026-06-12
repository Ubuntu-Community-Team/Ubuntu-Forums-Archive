---
title: "Adding a display mode"
date: 2010-09-07
forum: General Help
---

### Post by DavidS on 2010-09-07
I have a hand-held PC running Jaunty, and using the Poulsbo driver.

The screen is 800x480, and that is the only resolution available if I go to System - Preferences - Display.

However, the device is supposedly capable of 1024x768 (useful for dealing with windows which are too big for the screen).  Certainly the Windows XP version of the computer can achieve this.

Since the hardware is capable of showing 1024x768, I feel it should be possible to get this screen mode in Linux.  But how would I go about doing that?

The relevant section of /etc/X11/xorg.conf currently only consists of the following:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

David

---

