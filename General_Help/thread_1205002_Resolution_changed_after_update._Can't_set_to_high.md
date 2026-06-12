---
title: "Resolution changed after update. Can't set to higher."
date: 2009-07-05
forum: General Help
---

### Post by paulkruger on 2009-07-05
**[COLOR="DarkRed"]I just installed Ubuntu and everything was fine until updates and a reboot.[/COLOR]**

Prior to the updates I had a nice screen. When I let auto updates download and install recent patches and rebooted all I can get is 800 x 600 resolution.

It was much higher and nicer before but I don't have any options to go back to my former resolution any more?

Since I am totally new to this, any help would be appreciated.

I don't know how to determine the video card. It is a Dell Precision Workstation that is about 5 or 6 years old but a nice box.

Any ideas?  Thanks.

---

### Post by paulkruger on 2009-07-05
Anyone here?

---

### Post by merlinus on 2009-07-05
You might look in the screen and/or monitor sections of /etc/X11/xorg.conf to see what the settings are.

---

### Post by paulkruger on 2009-07-07
What am I looking for?

---

### Post by paulkruger on 2009-07-07
> **merlinus said:**
> You might look in the screen and/or monitor sections of /etc/X11/xorg.conf to see what the settings are.

**results:  Does not say anything useful that I can determine.**

----------
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

---

### Post by paulkruger on 2009-07-07
Keep in mind that the video was fine after the initial installation but resolution dropped after updating the kernal via the automatic updates.

What ever the update did it un-did a good graphics configuration.

---

### Post by CatKiller on 2009-07-07
If you run ```
lspci | grep VGA
``` in a Terminal window you should be able to find out what graphics card you're using.

It is possible for a new kernel to cause proprietary drivers to not work; I know that the NVidia driver needs kernel modules ("binary blobs") that will only work with a specific kernel and no one but NVidia can provide these for any given kernel. It's one of the drawbacks of closed-source software. Maybe this is what's happened to you.

EDIT: X's log is at /var/log/Xorg.0.log. You may or may not find the contents enlightening.

---

