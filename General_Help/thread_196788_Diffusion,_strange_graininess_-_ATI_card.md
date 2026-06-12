---
title: "Diffusion, strange graininess - ATI card"
date: 2006-06-14
forum: General Help
---

### Post by rupy on 2006-06-14
On solid colours (aside from white) if I closely I can see a lot of graininess and diffusion instead of clear colours.

I thought it was the colour depth or drivers, but I have set the depth to 24bit and the drivers are definitely loaded fine.

Does anyone have any ideas of what it could possibly be? How do I make 100% sure that my X is running at 24bit? (I have set it in xorg.conf).

---

### Post by scxtt on 2006-06-14
[QUOTE=rupy]Does anyone have any ideas of what it could possibly be? How do I make 100% sure that my X is running at 24bit? (I have set it in xorg.conf).[/QUOTE]do a "glxinfo" and you should see a lot of 24s in the last bit of the output (it's a depth reference), 2nd column, after the hex in the 1st column ...

fyi - the monitor i'm using now (at work, a 21" samsung) gets grainy every now and then - maybe you're having a monitor issue? [this is in windows using a Radeon X300] ...

---

### Post by rupy on 2006-06-16
Yeah I see 24's. 

Damn so its definitely not the depth. What else could it be?

---

### Post by scxtt on 2006-06-16
what if you take a screenshot and view it on another monitor? -- does it look the same?

---

### Post by starkes on 2006-06-16
theres a few different ati drives with varying qualities though...

for me, fglrx is a bitch to get working, and I can only get it working with the xorg-driver-fglrx package and a new libGL.so.1.2, but the radeon driver works just by putting radeon in your device section of your xorg.conf, except that on glxgears i get about 2/3 the framerate with radeon as i do with fglrx.

if you are using fglrx or ati, its easy enough to try the radeon drivers, just put radeon in there instead of fglrx or ati and it should work without downloading or farting around with anything. Maybe that will fix up the problem?

---

### Post by rupy on 2006-06-18
I took a screenshot and looked at it on another monitor and it was crystal clear.

What would be the recommended plan of action? Try the ati drivers?

---

### Post by scxtt on 2006-06-18
sure, you can try other drivers - but i'd try plugging in another monitor into your card and see if it's grainy as well ...

---

### Post by tuberculo on 2006-06-20
I have the same problem in Ubuntu. I am pretty sure that the problem is not the monitor. I have dual boot and the image is normal when I go back to WinXP. I've noticed this problem usually occurs when then computer is on for a while and the boots in Ubuntu.

---

### Post by rupy on 2006-06-30
I tried different drivers and a ton of other stuff and nothing... I wonder if it is the screen drivers? Could that be possible?

---

### Post by tuberculo on 2006-08-04
I think the problem is the driver. When I booted the LiveCD the image was normal.

---

### Post by rupy on 2006-08-06
ya u are right - when using the vesa driver the graphics are clear, its the fglrx driver that is causing this.

Does anyone have any ideas what to do from here?

---

