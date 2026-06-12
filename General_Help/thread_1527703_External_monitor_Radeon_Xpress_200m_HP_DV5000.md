---
title: "External monitor Radeon Xpress 200m HP DV5000"
date: 2010-07-09
forum: General Help
---

### Post by SyCo123 on 2010-07-09
Hi, I'm hoping to get the external VGA working on my Xubuntu laptop. I [posted a week ago]("http://ubuntuforums.org/showthread.php?t=1522309") in Laptops section but have yet to hear anything.

Can anyone help? 

This worked in XP when I dual booted but now XP is in a virtual machine, I have the full HDD :) but no projector. :(

---

### Post by bobcollard on 2010-07-09
> **SyCo123 said:**
> Hi, I'm hoping to get the external VGA working on my Xubuntu laptop. I [posted a week ago]("http://ubuntuforums.org/showthread.php?t=1522309") in Laptops section but have yet to hear anything.

Can anyone help? 

This worked in XP when I dual booted but now XP is in a virtual machine, I have the full HDD :) but no projector. :(
On your laptop screen with the external monitor plugged in, look at Display in the Xfce Settings Manager.  You may need to drop down to 60Hz and set the Resolution for your external monitor.  I also had to set my Power Manager settings to do nothing when the lid is closed in both AC and Battery.  I'm using a Samsung SyncMaster 2233 with a 21 1/2" screen.

---

### Post by SyCo123 on 2010-08-15
Thanks for the reply.Turned out this works
[http://promberger.info/linux/2007/12/20/external-monitor-on-thinkpad-x41-running-xubuntu-gutsy/](http://promberger.info/linux/2007/12/20/external-monitor-on-thinkpad-x41-running-xubuntu-gutsy/)

This didn't work first time 
```
xrandr --output VGA --auto
```
I had to run just 
```
xrandr
```
and from that output could change to 
```
xrandr --output VGA-0 --auto
```

and to set the right res
```
xrandr --output VGA-0 --right-of LVDS --mode 1280x800
```

and I'm in business!

---

