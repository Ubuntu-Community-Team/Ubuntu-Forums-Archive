---
title: "Ubuntu broke after chaning resolution"
date: 2009-08-29
forum: General Help
---

### Post by taddy_porter on 2009-08-29
I've had everything going fine with Jaunty except that my monitor wasn't being recognized and I was getting the wrong resolution. The usual gnome display settings box wouldn't work. Any time I clicked it, it would just hang blank and the screen would flash.

The KDE system setting display box would load. I have a Radeon 4350 using the ATI drivers. I tried connecting via DVI, but it would never work, so I went back to VGA and that would work, but at the wrong resolution. (as a side note, the DVI appears to be broken as I tried switching cards and the DVI wouldn't work past the BIOS screens).

Anyway, I plugged in both the DVI and VGA and this let the system identify my monitor and set the right resolution. The VGA was shown as CRT-1 and the DVI as DFP-1 or something similar. But the screen kept flashing. 

I tried going into the CRT section on the display screen and disabling it. My screen went blank. I waited for the box to reset it, and it did. Some where along the line the screen flashed to black, then went all white. CNT-ALT-Backspace did nothing, and neither did hitting the ALT-F keys. 

I hard booted. It went fine, I got the ubuntu logo and everything. Then, when it should have loaded an X screen, all I got was a blank screen. I have auto-login set, so I don't know if I got to GDM or not. Again none of the cntrl-alt funcions or backspaces did anything. My monitor reports it's receiving a 1680-1040 60hz signal (which frustratingly is what I was trying to achieve the first time).

I've tried re-setting the conf file, running the xorg -phigh command, I even tried putting a geforce 8600gt in there, but still the same thing. Also tried logging in as root and doing a startx, but nothing.

Any ideas what to do? I can get to a root prompt from grub, that's all I can get to. Not sure where to go from here.

---

### Post by wojox on 2009-08-29
Try running:

```
dpkg-reconfigure xserver-xorg
```

---

### Post by taddy_porter on 2009-08-29
I'm making progress now. I did the reconfigure xserver and reinstalled xserver. Now I'm getting past the login and into to gnome, and I'm getting my cursor, and I'm hearing the system sounds.

Unfortunately, I'm still getting a blank white screen. The Alt keys are working now, so I can get to a terminal. CNTRL-ALT-BACKSPACE does nothing. Oddly, I can still rotate the desktop cube. It's just nothing but white space.

---

