---
title: "Cracked LCD Virtual framebuffer"
date: 2009-08-16
forum: General Help
---

### Post by nthalk on 2009-08-16
How do you use xrandr or xorg.conf to make a virtual framebuffer that is SMALLER than my whole LCD but large enough for the working part of it?

I have used xrandr to create a fb, however it seems like I am not allowed to have unused monitor space:

```
$ xrandr  --fb 1024x900 --output LVDS --mode 1440x900 --pos 405x0
xrandr: specified screen 1024x900 not large enough for output LVDS (1440x900+0+0)
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  21 ()
  Value in failed request:  0x0
  Serial number of failed request:  28
  Current serial number in output stream:  28

```

I tried with xorg.conf, however that resulted the same failure.

I recently cracked my MacBookPro Revision 4 LED LCD along the right side for about 405 pixels.

This has caused the display to be fairly difficult to use, as all new windows tend to start upper left and can sometimes be hidden. I have looked into replacing the LED LCD and the cost is astronomical (I have since purchased a dell mini 10 with all of the fixings for less than the hardware LED LCD component).

Is it even possible to have the video device render a framebuffer of 1024x900 in a 1440x900 resolution and offset the framebuffer 405x0 from the top left of the monitor?

---

