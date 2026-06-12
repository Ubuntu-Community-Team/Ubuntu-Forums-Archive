---
title: "&quot;Frequency out of range&quot; message after GRUB"
date: 2011-05-11
forum: General Help
---

### Post by andy_blah on 2011-05-11
I've been having this problem ever since I updated the kernel version and reinstalled the video drivers. It happens after grub and before I log in with my account.
I know it wasn't a resolution related problem due to the fact that I had a compatible one set last time (I don't really think 1024x768 has any problems with my monitor), and the only thing left to modify is the vertical and horizontal refresh rate, and for that I tried running:
```
sudo dpkg-reconfigure xserver-xorg
```

as some forums/threads pointed, but it just returns a blank line and nothing happens (the threads were quite old since I couldn't find anything recent so I suppose it's outdated). So then, what do I do to reconfigure X? X.X

---

### Post by Grenage on 2011-05-11
> **andy_blah said:**
> I've been having this problem ever since I updated the kernel version and reinstalled the video drivers. It happens after grub and before I log in with my account.
I know it wasn't a resolution related problem due to the fact that I had a compatible one set last time (I don't really think 1024x768 has any problems with my monitor), and the only thing left to modify is the vertical and horizontal refresh rate, and for that I tried running:
```
sudo dpkg-reconfigure xserver-xorg
```

as some forums/threads pointed, but it just returns a blank line and nothing happens (the threads were quite old since I couldn't find anything recent so I suppose it's outdated). So then, what do I do to reconfigure X? X.X

Greetings,

What graphics card do you have, and what driver did you install?  If you can give us this information, plus your monitor make/model, then I could give you a basic xorg.conf that will hopefully help.

---

### Post by andy_blah on 2011-05-11
> **Grenage said:**
> Greetings,

What graphics card do you have, and what driver did you install?  If you can give us this information, plus your monitor make/model, then I could give you a basic xorg.conf that will hopefully help.

Thanks for the reply.
The video card model is NVidia 5500FX, the monitor is a Dell M782p (CRT).

---

### Post by Grenage on 2011-05-11
> **andy_blah said:**
> Thanks for the reply.
The video card model is NVidia 5500FX, the monitor is a Dell M782p (CRT).

Dells are nice and easy, their website spec lists are great; give this a whirl:

Backup your old config:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Create a new blank one:

```
sudo touch /etc/X11/xorg.conf
```

Then edit it using an editor of your choice:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Dell"
	ModelName "M782P"
	HorizSync 30 - 85
	VertRefresh 50 - 160
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "NVidia 5500FX"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection
```

That's a pretty basic config, which should give you 1024x768 using the nvidia driver. *Driver "nvidia"* can be replaced with *Driver "nv"* if you wish to use the open driver.

If it doesn't work, try adding a modeline to the monitor section:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Dell"
	ModelName "M782P"
	HorizSync 30 - 85
	VertRefresh 50 - 160
Modeline "1024x768_85.00"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
EndSection
```

That modeline tried to push 1024x768 at 85Hz

---

### Post by andy_blah on 2011-05-11
Thanks alot, I'll try typing what you gave me.
What's the difference between the open driver and the other one? I use their official driver (forgot to give the version: 173.14.30), because the one that is bundled with Ubuntu doesn't work (surprise surprise)
Also, considering the above, would I have to modify xorg.conf each time I reinstall the driver? (after kernel updates)

---

### Post by Grenage on 2011-05-11
> **andy_blah said:**
> Thanks alot, I'll try typing what you gave me.
What's the difference between the open driver and the other one? I use their official driver (forgot to give the version: 173.14.30), because the one that is bundled with Ubuntu doesn't work (surprise surprise)
Also, considering the above, would I have to modify xorg.conf each time I reinstall the driver? (after kernel updates)

Thu proprietary one is better at dealing with things such as hardware acceleration; I personally use it over the open driver, but I play games.  Some people are very much against closed source, so the open driver suits them.

The xorg.conf shouldn't need re-writing after an update, but it can't hurt to have a backup lying around.

---

