---
title: "System freezes after login"
date: 2010-02-06
forum: General Help
---

### Post by phredbull on 2010-02-06
I just installed 9.10, dual booting w/WinXP. Install went fine, update went fine, and everything seemed ok, including Windoze. I then decided to get rid of the fglrx drivers and use OSS, (ATI Radeon7500), according to this guide:
[http://ubuntuforums.org/showthread.php?t=1238129]("http://ubuntuforums.org/showpost.php?p=8448508&postcount=101")
(I had done this successfully before with a Wubi install on this same machine.)
I installed kernel 2.6.32 and rebooted, still seemed ok.
I then added the xorg-edgers PPA, and restarted. Everything went as normal until I logged in. I hear the startup sound, see the pointer, which turns into the spinning busy icon, then everything stops. No mouse movement, ctrl+alt+F2 does nothing, and the hdd activity light stops.

I booted into the recovery kernel and tried repairing packages, but when rebooting, still the same. I tried dpkg-reconfigure xorg-xserver and hal, but still the same. I tried booting with an older kernel, but still the same.

Not sure if this is related, but I also can't boot into WinXP now; it says hal.dll is missing and I need to re-copy it fron the install disk, which I don't have. I'm now running off of my live usb stick.

---

### Post by phredbull on 2010-02-07
Ok, I fixed my WinXP install, which I'm now using.

Any suggestions on how to fix my Ubuntu? Is Gnome broken, or did I mess up when installing the OSS ATI drivers? I've searched the forums for similar problems, and most of them seem to be unsolved, w/the OP reinstalling or downgrading. I've installed and reinstalled 9.10 like 4 times, and don't really want to do it again.

---

### Post by phredbull on 2010-02-08
I generated an xorg.conf file and edited the device settings to how I had them on my old Wubi install. Now when I try to login, the screen turns black, flickers a bit, I see a flash of text, then the login screen reloads. I saw a similar problem here in the forums, but the solution was to remove GDM and install KDM, and I don't want to do that 'cause my hardware is weak and puny! I'm still wondering if there was a problem installing the OSS drivers? Fglrx is gone for sure, so is it possible that I have no drivers at all?

---

### Post by phredbull on 2010-02-08
I can log into Gnome failsafe mode, but regular Gnome is still the same. I saw that the OSS drivers were installed, (according to Synaptic). I ran the System Test video tests and everything seemed normal there. Any suggestions? Anyone?

---

### Post by phredbull on 2010-02-08
bump

(I had to do it!)

---

### Post by phredbull on 2010-02-08
Never mind, I got it! I booted into recovery mode and did "sudo dpkg-reconfigure xserver-xorg" (again) and now I'm all good. Thanks for all the great advice!
](*,)

---

### Post by afrodeity on 2010-03-06
If you have the same problem again, you can also try this
[http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html)

---

