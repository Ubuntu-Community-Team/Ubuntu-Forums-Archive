---
title: "SOLUTION - Dual Monitors in Xubuntu"
date: 2010-11-26
forum: General Help
---

### Post by High Camp on 2010-11-26
Hi All

I was running Ubuntu but had to rebuild from scratch after trying to update to 10.10. I decided to go back to XFCE because I like it so much more. The only thing holding me back was the ability to use my projector. I did a lot of searching and could only find people with the same problem, no solutions. Thus, I'm posting my solution in the hopes it helps someone. 

Note, I actually found a thread (not on here) that said "the XFCE developers are aware of this problem and are not interested in correcting it".

The problem is, under Xubuntu you can run dual monitors but the display is cloned (same display on both screens), which is pretty pointless. I would assume this solution would work with any monitor, not just a projector but I'm not going to test it.

The solution is very easy and posted here: [https://wiki.ubuntu.com/X/Config/Resolution#How to setup a dual monitor]("https://wiki.ubuntu.com/X/Config/Resolution#How to setup a dual monitor")

Simply put, the author states that he/she created a file ~/.xprofile and put the following in it:
```
xrandr --output VGA1 --mode 1024X768 --rate 60

#Laptop right extra Monitor Left
#xrandr --output VGA1 --left-of LVDS1

#Laptop left extra Monitor right
#xrandr --output LVDS1 --left-of VGA1
```

I didn't want to load the profile every time since my projector isn't plugged in all the time. I created a shell script called dual_monitors.sh and put the following in it:
```
xrandr --output LVDS1 --left-of VGA1
xrandr --output VGA1 --mode 1280x800 --rate 60
```
I then put a launcher on my toolbar that runs that script (I tried putting the commands directly in the launcher but that didn't work for me).

One side note, it seems the monitors still have to be the same resolution. I tried to make the projector resolution bigger but that forced the laptop resolution to be too big so I couldn't access the bottom of my screen.

I hope that helps someone,

---

### Post by floydian_slip on 2011-09-11
Thanks for this info.

I was able to set up two monitors (laptop + extra) with two different resolutions by adding an extra line that specifies the resolution of my laptop monitor.

```

xrandr --output LVDS1 --mode 1366x768 --rate 60

```

Here is my script:

```

#!/bin/bash

# RESOLUTION SETTINGS
# This sets your VGA1 monitor to its best resolution.
xrandr --output VGA1 --mode 1280x1024 --rate 60
# This sets your laptop monitor to its best resolution.
xrandr --output LVDS1 --mode 1366x768 --rate 60

# MONITOR ORDER
# Laptop right, VGA1 monitor left
xrandr --output VGA1 --left-of LVDS1
# Laptop left, VGA1 monitor right
#xrandr --output LVDS1 --left-of VGA1

# PRIMARY MONITOR
# This sets your laptop monitor as your primary monitor.
#xrandr --output LVDS1 --primary
# This sets your VGA monitor as your primary monitor.
xrandr --output VGA1 --primary

```

Of course, you'll need to replace the resolution values in the "RESOLUTION SETTINGS" part to whichever the optimal values are for your own monitors. To find out what they are, just type

```

xrandr

```

in terminal, and see what the topmost resolution is for VGA1 and for LVDS1.

---

### Post by P05TMAN on 2011-09-11
Thank you both for your valuable input! Now I can try this with my TV as my second monitor!

---

### Post by steevven1 on 2011-11-11
This has all been VERY helpful. Thanks to those who contributed to it. I have run into one problem though: It seems that the left screen always gets the panels (meaning the left screen is always the "main" screen). What if you wanted the right monitor to be the main one?

EDIT: I tried "
xrandr --output LVDS1 --primary" and it didn't work, however, in the xfce "panels" settings, you can move panels to particular monitors :-)

---

### Post by BlakJakNZ on 2012-03-13
I've just installed 12.04b1 with a dual monitor setup on a Laptop (so it's single monitor when i'm not at the office.)

So far i've wound up with two scripts:


```

#!/bin/bash
# Based on http://ubuntuforums.org/showthread.php?p=11446000#post11446000,
# Modified for my needs 20120314 - BlakJak / BlakJakNZ.
# Sets LG E2041 20" LCD as Pri Display Left of Lenovo T510 Laptop Display.
# RESOLUTION SETTINGS
# This sets your VGA1 monitor to its best resolution.
xrandr --output VGA1 --mode 1600x900 --rate 60
# This sets your laptop monitor to its best resolution.
xrandr --output LVDS1 --mode 1366x768 --rate 60

# MONITOR ORDER
# Laptop right, VGA1 monitor left
xrandr --output VGA1 --left-of LVDS1
# Laptop left, VGA1 monitor right
#xrandr --output LVDS1 --left-of VGA1

# PRIMARY MONITOR
# This sets your laptop monitor as your primary monitor.
#xrandr --output LVDS1 --primary
# This sets your VGA monitor as your primary monitor.
xrandr --output VGA1 --primary
```And to revert to single display

```

#!/bin/bash
# see dualmonitors.sh for background.
xrandr --output LVDS1 --mode 1366x768 --rate 60
xrandr --output LVDS1 --primary
xrandr --output VGA1 --off

markf@hawkeye:~$ 

```

Having just moved to this from Ubuntu 10.10 and finding the latter was terrible at automatically adjusting display settings to disconnect my laptop (for a meeting or whatever) i'm relatively comfortable knowing that I have scripts that'll put me back where I need to be.  Wishing this could be automatically handled more gracefully though!

---

