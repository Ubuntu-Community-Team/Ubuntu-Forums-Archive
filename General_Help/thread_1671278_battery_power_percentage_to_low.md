---
title: "battery power percentage to low"
date: 2011-01-19
forum: General Help
---

### Post by perezomail on 2011-01-19
I know how to set and have set my net-book gz5 running on lucid to stay on at all times.
however unlike in xubuntu I don't have the option to change when the computer is critically low. I don't have the room to install xubuntu with my preferred gnome desktop wondered if anyone out thee knows where if there is a .config file that I can dictate the percentage of battery life before being considered critically low. 

ei now it seems to consider itself low at 15% which robs me of about 2 hours of usage 
id like to set it around 1%

---

### Post by psusi on 2011-01-19
You might want to leave it where it is at.  The lower you discharge the battery, the more you wear it out, so it is probably a good thing that it isn't letting you run it all the way down.

---

### Post by charileb000 on 2011-03-17
interesting reading

[http://tp0x45.blogspot.com/2009/01/critically-low-battery-settings-ubuntu.html](http://tp0x45.blogspot.com/2009/01/critically-low-battery-settings-ubuntu.html)
[http://sodoityourself.com/reviving-laptop-batteries/](http://sodoityourself.com/reviving-laptop-batteries/)
[https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/135548](https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/135548) (may not apply here, about no action when battery low)
if you do research on Li-ion batteries you will find that the more time spent hot and/or charged, the faster the deterioration.

---

### Post by Jouke74 on 2011-03-17
(Alt+F2) 'gconf-editor' navigate to apps > gnome power manager
There you will find a whole bunch of options under thresholds to change the times an/or ignore battery warnings.

---

### Post by nigou11 on 2011-03-17
This is probably go

---

### Post by psusi on 2011-03-17
> **charileb000 said:**
> 
if you do research on Li-ion batteries you will find that the more time spent hot and/or charged, the faster the deterioration.

*Dis*charged, not charged.  The deeper you discharge them, the more often you do so, and the longer they stay there, the more they deteriorate.  Manufacturers recommend not discharging more than 30-50% for maximum life span.  In other words, keep it above 50-70% charge.

---

