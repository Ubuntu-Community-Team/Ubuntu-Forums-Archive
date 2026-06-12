---
title: "Ubuntu 9.10 gets stuck at boot with a blinking login screen!"
date: 2009-11-16
forum: General Help
---

### Post by Alpyre on 2009-11-16
Sytem gets stuck while booting (from LiveCD or HDInstall):
It writes:

Ubuntu 9.10 username-desktop tty1
username-desktop login:

and the screen blinks together with my HD Led.

My hardware configuration is:
Asus P4T533C / Intel P4 2.4Ghz / Kingston 512MB RD Ram / Asus TI4200 128MB / SBlive! 5.1 / LifeviewII / Realtek RTL 8139

I want to experience Ubuntu in this computer of mine.

Thanks in advance for the help.

---

### Post by voxman69 on 2009-11-16
I've seen a lot of posts on this, and yesterday it happened to me too.
This worked for me:

Boot from a live-cd 
Hit Alt+F2 and type "gksu nautilus"
Go to Filesystem -> etc -> X11 and open xorg.conf
Look for the device section:

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


In mine above it says "nvidia" for Driver. Change that to "vesa". 

Save and reboot.


Now, once back, in your menu go to "System -> Administration -> Hardware Drivers" and chose the driver you want.

---

### Post by Giblet5 on 2009-11-16
Odds are, it can't figure out what your monitor is capable of and it's guessing.....wrong.

What is your monitor's best resolution and refresh rate?

Go look at the specs for it on the vendor's site. Post it here and I'll provide a config file that should get you running perfectly.

---

### Post by Giblet5 on 2009-11-16
> **voxman69 said:**
> I've seen a lot of posts on this, and yesterday it happened to me too.

I'm sorry, but that's not even close.

Alt+F2 only works from the GUI that OP does not have.

Drivers won't cause this problem. Even if they did, one would change "nvidia" to "nv" (not "vesa").

---

### Post by voxman69 on 2009-11-16
Yes, you're right about the GUI. I'm sorry, didn't read it carefully enough.

The other part however (vesa + driver) did the trick for me, so...

---

### Post by Giblet5 on 2009-11-16
The vesa driver is a subset of the nv (opensource nvidia) driver.

You're right. Kinda. vesa will work. nv will work better.

Driver problems don't manifest this way. Cable problems and non-compliant monitors do. You don't see this under Windows because vendors provide 'translation' files (.inf format) for their products. That gets it working despite the protocol failures. Vendors don't do that for Linux and we have to do it manually with the cvt or xrandr commands.

OP has a GeForce ti4200 card, so Xorg will handle it well once it knows what's hooked to the card.

This is a problem of DDC/CI and EDID protocol failure. It shows up in /var/log/Xorg.0.log. Xorg will attempt to use a VESA resolution when this happens, but not all monitors can handle VESA resolutions, resulting in this.

But I suspect that OP has gone off frustrated now after Alt+F2 didn't do anything and the goofy people on the Ubuntu forums can't quit bickering. So it doesn't really matter.

---

### Post by Alpyre on 2009-11-17
Problem is solved!
Thanks a lot for the discussion and ideas. I was suspecting it was a problem about my oldie GFX card just like you. But actually it wasn't. The problem is:

 Ubuntu doesn't boot successfully if a USB disk (any USB mass storage device) was plugged in before boot.

My flash disk was left plugged on the PC from another session. I've also experienced this with a USB external Harddisk on another system just to make sure.

Some other people are experiencing this as well. They suppose it happens randomly, it is mostly because they leave their USB disks plugged in randomly.

 I've also reported this as a bug in Ubuntu...

Thanks

---

### Post by sebpatu on 2009-11-26
Hello i had myself this bug, and after trying to update nvidia drivers nothing changed.
 
After reading this post, and the fact that usb drive plugged could make this bug happen, i tried a solution which worked:
In fact i had no USB drive plugged, but a second internal hard drive.
 
To be precise i had: a hard drive for ubuntu, and one for windows.
 
To unplug the second hard drive seemed to solve the issue. In fact it made it random. Maybe it was already random and i was not lucky :)
After activating the nvidia driver from ubuntu it fixed my issue.
 
Thanks.
 
Too bad this sort of install bugs appears cause it dont help Ubuntu to gain its simplicity public image against windows and mac os.

---

### Post by RodGer GR on 2009-12-28
> **Alpyre said:**
> Problem is solved!
Thanks a lot for the discussion and ideas. I was suspecting it was a problem about my oldie GFX card just like you. But actually it wasn't. The problem is:

 Ubuntu doesn't boot successfully if a USB disk (any USB mass storage device) was plugged in before boot.

My flash disk was left plugged on the PC from another session. I've also experienced this with a USB external Harddisk on another system just to make sure.

Some other people are experiencing this as well. They suppose it happens randomly, it is mostly because they leave their USB disks plugged in randomly.

 I've also reported this as a bug in Ubuntu...

Thanks

Can you please give a link to the bug that you filed?

I have a similar problem and it seems to happen when I have connected a usb mouse.
It's a friend's toshiba A 300 1-Lt laptop with GLRX graphics driver installed. 
I hope to find a solution because it is his 1st time trying linux and I wouldn't like to let him go disappointed back to windows...

---

