---
title: "Lost Display"
date: 2009-11-07
forum: General Help
---

### Post by Duskao on 2009-11-07
I removed my fglrx display drivers through synaptic and now when I boot up I am just getting text. If I try anything it says DISPLAY is not set. Help! I would prefer not to reinstall ubuntu 9.10. Plus this way I might learn something.

I have a radeon X4850 if that has anything to do with it. When I get it back up and running I would like to be using the X.org Radeon drivers.

---

### Post by amingv on 2009-11-07
Something similar happened in a machine I tested, the solution was removing the driver-generated xorg.conf, which asked for the (uninstalled) driver. Log into the terminal (do Ctrl+Alt+F1 if you can't see it) and input these commands:

```
cd /etc/X11
sudo mv xorg.conf xorg.conf.old
```

then type:
```
startx
```

And see if it comes up.

---

