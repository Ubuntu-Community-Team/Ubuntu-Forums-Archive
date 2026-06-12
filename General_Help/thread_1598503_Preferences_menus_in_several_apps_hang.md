---
title: "Preferences menus in several apps hang"
date: 2010-10-16
forum: General Help
---

### Post by Danielson1218 on 2010-10-16
Hello all,

For a few applications under Ubuntu Netbook Edition 10.10, upon trying to close a preferences menu (whether or not anything was changed,) the window hangs and needs a force quit. Applications I've noticed exhibiting this problem so far are:

deadbeef
snes9x-gtk

If I DO change any settings, I see that they've stuck when I reopen the program.

In case it will help diagnose the problem, a few apps whose preferences menus close normally are:

gimp
transmission
audacity (although preferences will not reopen after being closed once)

Any ideas? Thanks.

---

### Post by kerry_s on 2010-10-16
if there maximized, try unmaximizing/restore & use the normal window close button.

---

### Post by lazyr on 2010-12-27
I have the exact same problem.

I found out it's caused by the indicator-applet-appmenu. As soon as I remove this from the panel, the problems disappear.

Can you confirm this? Maybe we can create a bug report for this.

---

