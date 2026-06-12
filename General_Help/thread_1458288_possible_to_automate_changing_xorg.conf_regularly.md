---
title: "possible to automate changing xorg.conf regularly?"
date: 2010-04-19
forum: General Help
---

### Post by mateomiguel on 2010-04-19
I have a bit of a strange setup in that I take my laptop, which runs Ubuntu 10.04, to work and back home with me every day.  At both locations I use an external monitor.  However, at work, the monitor is rotated counter-clockwise to help me look at documents better.  

I've soldiered through and found out everything that I need to set this up, so I've got a nice xorg.conf that works at both places.  Well, almost.  It has a section for an external monitor which looks like this at work:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ADE J2200W"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
    Option	   "Rotate"	"CCW"
EndSection
```

Then, when I go home, I manually edit the file to comment out the rotation line and restart my computer.  Every day.

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ADE J2200W"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
    #Option	   "Rotate"	"CCW"
EndSection
```

Everything works perfectly except that I don't enjoy manually editing config files every single day.  Is there some way I can automate this process somehow?  Ideally my computer would detect which monitor is plugged in and automatically go with the correct configuration.  Is that possible?

---

### Post by asmoore82 on 2010-04-19
If you are using any ubuntu that came out within the last year,
you should be running with no xorg.conf at all.

Then, you can just use the `xrandr` tool to switch setups on-the-fly.
Single/Dual/Triple Monitor, Rotated, Resized and all
with no editing config files and no re-starting X.

After you figure out the exact xrandr command for the setup you want,
you just put it into a launcher or keyboard shortcut and you can switch anytime.

A command to set up my laptop like that would look like this:
```
xrandr --ouptut LVDS1 --mode 1280x800 --output VGA1 --mode 1024x768 --right-of LVDS1 --rotate left
```

And your best friend command is
```
xrandr --auto
```
^I have this mapped to the keyboard shortcut Alt+F7

See ```
man xrandr
```

---

### Post by mateomiguel on 2010-04-21
Even if I'm using an nvidia card?

---

