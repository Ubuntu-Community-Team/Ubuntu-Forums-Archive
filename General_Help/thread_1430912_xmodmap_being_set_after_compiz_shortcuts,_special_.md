---
title: "xmodmap being set after compiz shortcuts, special keys are broken on login"
date: 2010-03-15
forum: General Help
---

### Post by birnam on 2010-03-15
I'm using 64bit Karmic Kubuntu. I have a Logitech G15 (v2) keyboard and am using g15daemon 1.9.5.3 compiled with libg15 1.201. I use Compiz commands to set shortcuts for my G keys.

In order to use my G15 correctly (with the G1 key showing up as G1, etc.) I have to use a custom ~/.Xmodmap -- otherwise the keycodes are off for some reason, e.g. G6 looks like XF86HomePage, etc. This would almost be acceptable, but the G4 keycode doesn't match any keysym, so it basically doesn't exist without .Xmodmap

The problem is that compiz commands seem to get loaded before the .Xmodmap is run. So when I first login, compiz thinks the keys it's providing shortcuts for don't exist. The workaround is to open up the ccsm, uncheck "commands", wait a second, then check it again. And tada, everything works because now the keys exist.

Over the last eight or nine months this has grown from being mildly curious to downright annoying.

How can I load Xmodmap first? I've tried putting the Xmodmap customization in /etc/X11/Xmodmap, but apparently that doesn't work anymore. That is, it has zero effect. I've tried calling it manually from /etc/X11/Xsession and /etc/kde4/kdm/Xsession and neither do anything at all. /etc/X11/xinit/xinitrc is the same. If I call it through a script in Autostart then it gets called too late and I have the same compiz problem as before.

At this point, I'm not sure what is and isn't getting called at all. When I was trying to add the xmodmap command to /etc/X11/xinit/xinitrc and not seeing any effect, I also added "echo 'test' > /tmp/xinitrc-was-called" just to see if xinitrc was being processed at all, and it appears that it wasn't.

I'm feeling quite frustrated over this. :confused:  Any ideas, anyone?

---

### Post by birnam on 2010-03-22
I'll try a bump...  Still quite frustrated by this.

---

