---
title: "Fresh install of 12.04 Desktop freezes right after login"
date: 2012-08-15
forum: General Help
---

### Post by yang on 2012-08-15
I did a clean install of Ubuntu 12.04 Desktop onto my Dell XPS 410n desktop with an Nvidia GeForce GTS 8800 graphics card.  I always enable auto-login-to-desktop.

The first boot went OK, except that as soon as the desktop showed up, the screen looked strange: the desktop was too big for the monitor and appeared off center.  I managed to bring up the Screen settings panel, and switching away then back to the current resolution fixed things.

During this boot I was prompted to (and did) install/activate "version current" of the Nvidia drivers (from 173).  I also upgraded some 300+ packages via Update Manager.

After rebooting and the desktop appeared, it took about a minute after the wallpaper appeared for the menu bar to appear.  Although I could move the mouse, nothing was responding to my clicks/key presses.  I could, however, ctrl-alt-f2 (each time it would take 15s or so to actually switch to the terminal, though).

When I ctrl-alt-f7 back to the desktop, the screen is just black, though I do see my Network Manager menu (one of the things I tried clicking before) a in a strange artifacted manner.  That was the last response I was able to get from my system.  Subsequent switches away then back to ctrl-alt-f7 just showed black screens.

I looked through some logs but the only thing possibly suspicious I noticed was in Xorg.0.log:

```
[    22.045] (EE) Failed to load module "nv" (module does not exist, 0)
```

But the nvidia driver is loaded.  Any ideas?  Per [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze), here's lshw, lspci, kern.log, dmesg, syslog, and Xorg.0.log:

[https://gist.github.com/3365293](https://gist.github.com/3365293)

TIA.

---

