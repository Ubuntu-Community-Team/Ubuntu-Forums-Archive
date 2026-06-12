---
title: "Yet another 1280x800 915resolution problem"
date: 2006-06-07
forum: General Help
---

### Post by sheilnaik on 2006-06-07
Let me start off by saying that I REALLY didn't want to post this question, but I've been trying to get this working for over a day and have had no success.

I have a Dell 700m and I'm using Dapper on it.  The native screen resolution is 1280x800, but Ubuntu only recognizes 1024x768, so naturally I'm going to have to use 915resolution to fix this problem.

I tried the instructions on the topics here - [http://www.ubuntuforums.org/showthread.php?t=191273&highlight=1280x800](http://www.ubuntuforums.org/showthread.php?t=191273&highlight=1280x800) - and here - [http://www.ubuntuforums.org/showthread.php?t=190237&highlight=1280x800](http://www.ubuntuforums.org/showthread.php?t=190237&highlight=1280x800).

Here's a list of the modes that display when I do a sudo 915resolution -l:

```

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 855GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $29f
Mode Table Entries: 39

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 24 bits/pixel
Mode 7c : 1280x800, 8 bits/pixel
Mode 7d : 1280x800, 16 bits/pixel
Mode 7e : 1280x800, 24 bits/pixel

```

My xorg.conf file (the Screen and Display part) looks like this:

```

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

I don't get it.  I told 915resolution that I want 1280x800, I added it to xorg.conf, and it still won't work.  855resolution worked fine in Breezy (since then, I have uninstalled and reinstalled Ubuntu), so there's no reason why 915resolution shouldn't work.  What am I doing wrong?

- Sheil

PS.  After I change settings, I'm doing a Ctrl+Alt+Bkspace to test out the new settings.  From what I understand, this will not be affected by the fact that the 915resolution script needs to be initialized everytime your computer boots up, but maybe I'm wrong.

---

### Post by sheilnaik on 2006-06-07
I added a proper Modeline to my Display.  Still doesn't work...

---

### Post by sheilnaik on 2006-06-07
Sorry to bump, but can anyone help?

---

### Post by yopnono on 2006-06-07
And you have tried to add the resolution to the 915resolution file in /etc/default
```

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=3c
#
# and set resolutions for the mode.
#
XRESO=1280
YRESO=800
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=8

```

---

### Post by sheilnaik on 2006-06-07
I hate it when this happens..

Now, all of a sudden, the resolution displays fine.  No problems.  The system actually **crashed** and when it rebooted, everything works perfect.  This is why I hate computers sometimes...

Thanks for your reply yopnono.

---

### Post by ahh_dee on 2006-06-08
I had that problem also so this is what i did

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` - to back things up

```
sudo /etc/init.d/gdm stop
```

```
sudo dpkg-reconfigure xserver-xorg
```

```
sudo /etc/init.d/gdm restart
```

then restart X and it should work =)

---

### Post by halfthelaw on 2006-07-07
I have similiar problems, in that I can't get 32bit support at 1280x800. 915resolution says this should be availible (and it works in Windows), but if I try to set 32bit in xorg.conf, the X server will crash on startup with an error message that 32bit isn't support by the i810 drivers. Any idea how I can fix this?

---

