---
title: "Ubuntu CLI"
date: 2012-04-26
forum: General Help
---

### Post by Intrepid272 on 2012-04-26
Hi all,

I just installed the Ubuntu CommandLine-only, and now I'm trying to install x and FluxBox as per this guide: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems). I have installed it correctly, and everything works, but my problem is this:

Suppose I run flux in the first console (ctrl + alt + f1). I want to run flux, and be able to switch to the second console (ctrl + alt + f2), do whatever, and then switch back to the first console (ctrl + alt + f1) and have my flux wm still running.

Is this possible? If so, how?

---

### Post by JKyleOKC on 2012-04-26
Yes, it's possible, at least it is with the XFCE window manager that I use, and with every window manager I've tried in the past. The trick is that when the X Windows Server launches to provide your GUI, it creates a new virtual terminal, usually on Ctrl-Alt-F7 but I've also found it at F8 sometimes. The Ctrl-Alt-F-key switch works across the board, so you can simply try it and see whether this still does what you want in fluxbox (which is one of the managers that I've not tried).

When the system boots up, it creates six virtual terminals, and initially turns control to tty1. From there, you can switch any way you want to. If you have enough RAM resources, you can probably even run different window managers in each of the six; each time one of the managers launches the X server, an additional virtual terminal gets created for its use, and the launching terminal "goes to sleep" until you sign out of the graphic interface.

I hope this helps...

---

