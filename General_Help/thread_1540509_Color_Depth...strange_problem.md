---
title: "Color Depth...strange problem"
date: 2010-07-27
forum: General Help
---

### Post by TDrakeHI on 2010-07-27
Ok, I have been looking up information about how to change the monitor color depth so that I can resolve the "white square around curser" in Google Sketchup through wine.  

Everyplace says I need to edit my xorg.conf file to adjust the color depth...problem...there is no xorg.conf.  I have used sudo find / -name xorg.conf, nothing, I have grepped the find / command and have come up with a few zip and asst other file names with xorg.conf in the name, but no xorg.conf.  What am I doing wrong??  How do I change the color depth?  I know how to change the resolution and even use 2 monitors, but nothing about color depth in any of the admin or preferences widgets.

---

### Post by LegendofTom on 2010-07-27
Use:
```
locate xorg.conf
```

Should be here: /etc/X11/xorg.conf

Then all you need to do is open that up and change your Depth to whatever you desire.

Legend

---

### Post by TDrakeHI on 2010-07-27
Nope, no go.  here is the paste from the terminal:

```
tim@tim-laptop:/etc$ locate xorg.conf
/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz
tim@tim-laptop:/etc$ 

```

Any other thoughts??

---

### Post by TDrakeHI on 2010-07-27
Got it figured out.  Found another post that gave details how to make my own xorg.conf when there was none.  

[http://ubuntuforums.org/showthread.php?t=1333708](http://ubuntuforums.org/showthread.php?t=1333708)

That solved it for me.  Made my own, troubleshot it, found out I was already running in 24-bit.  Problem solved.  Thank you for your help.

---

### Post by LegendofTom on 2010-07-27
Glad to hear you got it figured out.  Welcome to the forums.

Legend

---

