---
title: "How do I enable Compiz with dual head monitors?  ATI card..."
date: 2009-12-12
forum: General Help
---

### Post by switch10 on 2009-12-12
I have the Radeon Xpress 200M ATI card.  I have a laptop screen as well as another monitor hooked up to the laptop.  I can run compiz only when the laptop screen is "mirrored" onto the monitor.  I want to be able to run compiz while using a "big desktop" kind of setup.  

I can run the the "big desktop" set up when compiz is disabled.  While "big dektop" is on, if I go to System>Preferences>Appearance>Visual Effects, and try Normal or Extra, it says "Searching for available drivers".  Then it says "Desktop effects could not be enabled".  

Is it possible to edit my Xorg.conf file to make this work?  If so what exactly do I need to do?

here is my Xorg.conf with both monitors

```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2560 800
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

---

### Post by bluelamp999 on 2009-12-12
AFAIK you can only run Big Desktop up to a certain resolution in Compiz. Your dual display setup probably exceeds this...

---

### Post by switch10 on 2009-12-12
That's a bummer...  Is this a Compiz issue or does it have to do with my graphic card??

Would it be possible to write a script or something, so when my monitor and my laptop screen are on, ubuntu would would automatically boot into big desktop, and when my monitor is off or unplugged, Ubuntu would know I just have my laptop screen to work with, and I could have Compiz enabled...

I hope that makes sense :)

Thanks for the help

Dave

---

### Post by drewsus on 2009-12-12
Compiz can only work with a maximum virtual desktop resolution of 2048x2048

Arranging your monitors side by side is your problem. What I do to get around this is arrange my monitors one on top of the other. 

It seems you want both your monitors to be at a resolution of 1280x800

I use xrandr

an example of code to run is (assuming your external is VGA1 and your laptop monitor is LVDS1): 

```
xrandr --output VGA1 --mode 1280x800 --pos 0x0 --output LVDS1 --mode 1280x800 --pos 0x799
```

This will create a virtual desktop with the external monitor above the laptop monitor with a slight overlap of one pixel. This is keep for making your external the main monitor (ie. it will have your docks and panels on it - if you want these on your laptop monitor change the last part from "799" to "800")

You can find out the suitable names to replace "VGA1" and "LVDS1" with this command:
```
xrandr -q
```
And of course, man is always helpful:
```
man xrandr
```

and example of the output I get with my external monitor disconnected using **xrandr -q** (Im using an Acer Aspire One):
```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
   1024x600       60.0*+
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1
```

Furthermore, the first line of code I provided can be set to a start up command.

If you have anymore questions...

---

### Post by switch10 on 2009-12-13
Beautiful!!!

Thanks a lot.  I can deal with this.

---

### Post by drewsus on 2009-12-13
Furthermore, I made a script to toggle dualscreen on and off:
```
#!/bin/sh
if xrandr --prop | grep -q "current 1024 x 600"
then
xrandr --output VGA1 --mode 1280x960 --pos 0x0 --output LVDS1 --mode 1024x600 --pos 0x959
else
xrandr --output VGA1 --off --output LVDS1 --auto
fi
```

You should note that the part "current 1024 x 600" should be changed to your default laptop monitor resolution. And, the 'then' statement should also be changed accordingly. Also, note the spacing. 
This is just an example ;)

Drewsus

---

### Post by switch10 on 2009-12-14
> **drewsus said:**
> Furthermore, I made a script to toggle dualscreen on and off:
```
#!/bin/sh
if xrandr --prop | grep -q "current 1024 x 600"
then
xrandr --output VGA1 --mode 1280x960 --pos 0x0 --output LVDS1 --mode 1024x600 --pos 0x959
else
xrandr --output VGA1 --off --output LVDS1 --auto
fi
```

You should note that the part "current 1024 x 600" should be changed to your default laptop monitor resolution. And, the 'then' statement should also be changed accordingly. Also, note the spacing. 
This is just an example ;)

Drewsus

Thanks Drewsus,

what do you mean by note the spacing though?

---

### Post by drewsus on 2009-12-14
make sure its "current 1024 x 600" not "current 1024x600" :) (or whatever your default resolution is)

---

### Post by switch10 on 2009-12-16
> **drewsus said:**
> make sure its "current 1024 x 600" not "current 1024x600" :) (or whatever your default resolution is)

Perfect.  Thanks..

---

