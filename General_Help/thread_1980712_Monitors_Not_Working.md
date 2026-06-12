---
title: "Monitors Not Working"
date: 2012-05-15
forum: General Help
---

### Post by Ubun2to on 2012-05-15
A few days ago, I found an old VGA monitor lying around (undamaged, since it worked when I booted Windows 7). However, I have a DVI-D port on my computer, with an adapter for my other VGA monitor, and the only other (enabled) port was an HDMI port.
Long story short, the way HP setup the graphics cards in the BIOS, only one can be running at a time, so I had to buy a converter to change the analog signal into a digital one that is usable with the HDMI port. There were 2 other ports-a VGA and DVI-D, but they were on the integrated graphics card, not the ATI, and I like being able to play my games, so that isn't an option.
Today, the converter arrived, and I eagerly plugged it in. When I booted to Ubuntu, it refused to do anything BUT mirror the original one, and the image was vertically squashed, and I can't fix it on the OSD.
So, I tried to get it to accept the fact that I wanted to use this second display, and what do you know, I set both to 800*600, and it works (although it is unbearably low res). Any other resolution gives me an error message. So, I try setting it to 1024*768, and the screen goes black (well both screens do, for that matter).
What I want to know is why did it go black, why does it refuse to do anything but mirror it, and how do I fix it?
Also, if this helps, the working monitor is displayed as a Dell something, and the one I've been having trouble with is displayed as some HDMI device.
Edit-I've gotten back on, and this is the error I recieve:
```
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: requested position/size for CRTC 148 is outside the allowed limit: position=(1280, 160), size=(width, height), maximum=(1920, 1920)
```

---

### Post by Ubun2to on 2012-05-17
Nevermind-HP lied to me, and I contacted a friend who fixed it.

---

