---
title: "46'' lcd screen resolution."
date: 2010-11-18
forum: General Help
---

### Post by cheeseheadfromwisconsin on 2010-11-18
Does ubuntu support a 46 inch monitor?  I have my tower hooked up to my big screen at home with a hdmi cable and the screen is really really to big, as in you can only see the purple background. No applications places or system or anything. When i switch to a lower resolution the screen is cropped.

---

### Post by efflandt on 2010-11-18
What video card/chip do you have?  Are you using default or proprietary video drivers?  And what is the "native" resolution of your 46" screen?

With 32" LG 1080p HDTV (which apparently X thinks is 52") connected DVI to HDMI or straight HDMI with nvidia drivers, if I set the TV to 16:9 it ends up slightly over scanned (cut off around edges).  But if I set the TV to "just scan" it matches itself to the signal it is receiving and displays perfectly for 1920x1080, 1360x768, or 1280x720.

Doe your TV itself have any screen adjustments for HDMI?  If you are using default video drivers you could play around with xrandr.  But with proprietary video you may need to play around with modelines in /etc/X11/xorg.conf if the app for that type of video does not have a proper mode.

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

