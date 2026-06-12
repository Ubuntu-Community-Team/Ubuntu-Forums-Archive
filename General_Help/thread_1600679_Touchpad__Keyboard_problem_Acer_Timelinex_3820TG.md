---
title: "Touchpad / Keyboard problem Acer Timelinex 3820TG"
date: 2010-10-19
forum: General Help
---

### Post by smokyink on 2010-10-19
Hello, I need some help with my laptop.

Everything was working perfectly ok up to the point that I decided to try out (Fn+F7) ie switch off touch pad. 

laptop model : Acer timelineX 3820TG.

The hardware works perfectly... tested with windows (also works at log in screen in linux).

The odd thing is that when I am at the log-in screen and use the  combination Fn+F7, the touch pad works, but right after log-in it stops  working...:confused:

Please someone, anyone help....and if you need output of any commands or logs I will be glad to post them, I just don't really know what/where to look for this problem...

----------------------------------------------------------------------------------------------------------------------------
EDIT: I found my own solution ... kind of... 

   So for anyone with the same problems :

It turned out that gnome-settings-daemon has its own switches for the touc hpad and when system boots with disabled by (Fn+f7) touch pad, gnome-settings-daemon has its switch as enabled. Thus the problem : one presses the button, hardware enables touch pad and gnome-settings-daemon disables it... 

Solution source: [https://bugzilla.redhat.com/show_bug.cgi?id=600650](https://bugzilla.redhat.com/show_bug.cgi?id=600650) (comment 13)

"The workarround of doing:  gconftool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean true "

---

