---
title: "Problems with Ubuntu 9.10"
date: 2010-01-15
forum: General Help
---

### Post by watzen on 2010-01-15
Hi! 
Never touch a running system...I just upgraded from Ubtuntu 9.05 to 9.10. That was no good idea...
Now my desktop is pitch black, like any apps I start in fullscrenn mode and I am not able to load any wallpapers.

Anyone know a solution?

Or just kick off this f...... update and install new (yippie!)?
It work so wonderful before...

cheers

---

### Post by deveric on 2010-01-15
There seems to be a few things going on that I can decipher:

-Your X manager is not starting up, is this correct? or can you see your mouse movement and whatnot?
-Hard drives are not mounting, what errors are you getting on this?
-What logon is required to access your hard drives?

---

### Post by watzen on 2010-01-15
Thanks for quick reply!

I fixed the problem with the HD. It was just the Keyboard in English instead of German.

I can see the mouse movement on the screen, but that's all, everything else is just black.
I can also open folders on my desktop (I can't see them, but I know were some of them ought to be).
I'm not really a Ubuntu/Linux professional, so I don't know if my X Manager is starting up...
if so, how do I know/fix it?

Thanks

---

### Post by ajgreeny on 2010-01-15
I suspect you are running an ati card with the open source driver and a resolution above 1024x768.  If that is so, right click on the black desktop and use the "Change desktop background"  to get to the appearance window.  On the Effects tab, choose none, then logout and back in again to restart x.

If your problem is the same as mine was, you will now have a desktop as before.  You can make that your default, ie, no compiz, or you can try editing the /etc/X11/xorg.conf file, after backing it up, of course, to change the default colour depth to 16, which may allow you to continue to run compiz etc etc.  Here is my xorg.conf as an example.

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
I hope this helps you and you get back your desktop.

---

### Post by watzen on 2010-01-15
Yeah, thanks!

I deactivated the effects in the "Change desktop background" Menue, and I got my desktop back!

For now it's working & I don't have the time & nerves to try that code stuff (I'm not really used to it...)

Let's see how it looks when I start my computer the next time...

Hopefully the same as now!

If not, I'll try your further suggestions or I'm back here again..(hopefully not)

Cheers & Thanks

---

