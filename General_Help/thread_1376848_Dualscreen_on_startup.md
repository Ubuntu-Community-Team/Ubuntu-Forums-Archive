---
title: "Dualscreen on startup"
date: 2010-01-09
forum: General Help
---

### Post by drewsus on 2010-01-09
I am using Ubuntu Karmic 9.10 on an acer aspire one. 
I have an old CRT external monitor

I cant get dualscreen to work on startup [the way I want it to]
No matter what I do, dualscreen starts with the laptop monitor positioned to the right of the external and compiz is turned off. 
What I want is the external above the laptop monitor and compiz on. 

I created /etc/X11/Xsession.d/45custom_xrandr-settings as suggested here: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Now_automate_it_on_login](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Now_automate_it_on_login)
and put the following in it:
```
xrandr --newmode 1440x900_59.90 106.29  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
xrandr --addmode VGA1 1440x900_59.90

xrandr | grep "VGA1 connected "
if [ $? -eq 0 ]; then
	(sleep 2; xrandr --output VGA1 --mode 1440x900_59.90 --pos 0x0 --output LVDS1 --mode 1024x600 --pos 0x899) &
else
	xrandr --output VGA1 --off --output LVDS1 --auto
fi
```

The first two lines seem to get executed (as doing 'xrandr' in terminal shows the new VGA1 mode) but the output options seem to be ignored and as I mentioned, defaulted to compiz being turned off and the monitors being placed side by side. The reason I want the monitors one on top of the other is so that compiz is not disabled. I can run the command to do so AFTER logging in, but I dont want to have to.

Any help would be great!

---

### Post by scouser73 on 2010-01-09
Well my suggestion is for nVidia graphics cards only but here goes.

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

---

### Post by drewsus on 2010-01-09
Thanks for the quick reply! Unfortunately the AAO has an intel chipset.

Furthermore, I tried adding the line "xrandr --output VGA1 --off --output LVDS1 --auto" to all the "Default" scripts in /etc/gdm/ as well as "Xsession" but the default of VGA and LVDS enabled SIDEBYSIDE (with compiz getting turned off) is very persistent! 
I cant figure out how to override it! 
Where is this setting being initiated?

I want to have my setting to be applied before this default and to stop it from trying to be set.

---

### Post by drewsus on 2010-01-10
bump

---

