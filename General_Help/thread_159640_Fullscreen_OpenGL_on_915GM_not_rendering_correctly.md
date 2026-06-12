---
title: "Fullscreen OpenGL on 915GM not rendering correctly?"
date: 2006-04-13
forum: General Help
---

### Post by josh2112 on 2006-04-13
I have a Dell Latitude D510 with Intel 915GM video running Kubuntu Breezy.  Certain of the KDE OpenGL screensavers (in particular the 'particle-based' ones, Flux, Gravity, Particle Fountain, Solar Winds, etc.) only render on the top half of the screen.  The bottom half is blank.  When I click Setup to go into a screensaver's options, the little window that shows you what the screensaver will look like only shows the bottom 1/3 or so!  Weird...

Furthermore, I think the screensavers that are exhibiting these problems are also rendering upside down... based on watching the same screensavers on another computer I have (also running Breezy).

Here is some info that may help... from glxinfo:

```

...
direct rendering: Yes
...
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.3.2
...

```

From xorg.conf:

```

Section "Module"
    Load    "GLcore"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
    Load    "synaptics"
EndSection
...
Section "Device"
    Identifier    "Intel Corporation Intel Default Card"
    Driver        "i810"
    BusID         "PCI:0:2:0"
EndSection

```

Is it possible that something in the i810 driver is making these GL screensavers draw vertically flipped and off-center?  The regular desktop and non-GL screensavers all look great.

---

### Post by rorschach on 2006-04-14
I have the same video chip (intel i915gm) and my glxinfo/xorg.conf reflect the same.
I asked around on the #wine and was told that the mesa drivers aren't actually dri/opengl capable for this chipset, regardless of the output we are seeing on those files (my problem stems from a wine issue.)

From what I learned, we need to find chipset-specific drivers for i915gm.

I am going through dri.freedesktop.org one at a time and trying to find one of the snapshots that will work. (I swear, once I'm done with this process, I'm writing a how-to for video, multimedia, wine, etc for this hp laptop o'mine)

I'll let you know if I find anything. Let me know if you make progress, ok?

Good luck!

---

### Post by Nathaniel on 2006-05-31
(I know this is an ancient thread, but I'm still having the same problem and even as Dapper's coming out tomorrow, it still doesn't work in Breezy)

I'm having the exact same problem. I've looked like a madman for some better drivers, but every site or thread I read tells me to use the i810-package. I haven't really tried to change xorg.conf myself, since I don't really know what to change.

Is there ANYONE out there who knows a better driver for me?

I'm using a Thinkpad T43 with intel i915 chipset

---

### Post by josh2112 on 2006-05-31
I've found a bug that looks very similar: 

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/43052]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/43052")

Also using Intel 915gm.  The bug was filed about a month ago and confirmed, hopefully there will be a fix for it pretty soon.... ?

---

### Post by Nathaniel on 2006-05-31
I installed xscreensaver (running Kubuntu which has its own screensaver daemon) and tried GL slideshow and Flurry, they both worked just fine (and with great framerate, I might add)

Maybe it's just kubuntu's screensavers?

---

### Post by josh2112 on 2006-05-31
[QUOTE=Nathaniel]Maybe it's just kubuntu's screensavers?[/QUOTE]

Except that whoever filed the bug report has the same problem with Amarok visualizations also....

Or, maybe there's some KDE "helper code" for OpenGL (to set up viewports & stuff) that Amarok and KDE screensavers are both using, and the problem is in there?

I'll switch to xscreensaver though, thanks for the tip.

---

### Post by geos2 on 2006-07-26
same problem on i950, amarok and screensavers... bzflag is ******...

argh.

---

