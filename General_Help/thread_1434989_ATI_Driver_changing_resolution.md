---
title: "ATI Driver changing resolution"
date: 2010-03-21
forum: General Help
---

### Post by theLumberjack4 on 2010-03-21
I installed the ATI driver and rebooted.  The resolution then has been changed to one that cannot be displayed by my monitor.  So I look around and find that I can use (in recovery mode) ```
sudo nano /etc/X11/xorg.conf
```to put in the specs for my monitor.

It works.

Then I'm trying to us PlayOnLinux and it tells me I don't have any 3D acceleration.  So I re-install the driver and reboot and my resolution is once again not being displayed.
I go back to look at my xorg.conf and my monitor specs aren't there anymore.  So I put them in again, write out and reboot.  However it's still in a resolution my monitor can't display.

The specs for my monitored I added to the end of xorg.conf like so:
```
Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"Dell"
	ModelName	"E196FPf"
	HorizSync	30.0 - 110.0
	VertRefresh	50.0 - 150.0
	Option	"DPMS"	"True"
EndSection

```
I'm new to Ubuntu and I found the specs in that format on another forum on a rather old post that I found through google.

My Windows XP is really starting to piss me off, I miss my Ubuntu, so help is very much appreciated :D

---

### Post by Ozymandias_117 on 2010-03-21
Not sure if this will help you, but here is mine.

```
Section "Monitor"
	Identifier   "0-DFP3"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection
```

---

### Post by Ozymandias_117 on 2010-03-21
Oh... also, just so you know. If you move your xorg.conf out of /etc/X11 when you reboot, it will automatically make a default one. That may fix your problem if you'd rather not mess around with editing it.

---

### Post by theLumberjack4 on 2010-03-21
Thanks Ozymandias, I added some of the options such as PrefferedMod and TargetRefresh but it still booted in a resolution my monitor couldn't display.

I feel like this was an obvious quick solution, I deleted the driver line xorg.conf and booted without problem.

However that still leaves me out of a driver :(

---

### Post by Mark Phelps on 2010-03-21
> **theLumberjack4 said:**
> However that still leaves me out of a driver :(

What model is your card? ATI dropped support for lots of cards last year.  If yours is not one of the newer HD 3x/4x/5xc cards, there will be no ATI driver that supports it.

---

### Post by theLumberjack4 on 2010-03-21
It's a radeon HD 3450

---

