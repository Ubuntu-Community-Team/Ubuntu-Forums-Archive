---
title: "Works perfectly on an AMD Athlon Desktop, but fails on a centrino laptop"
date: 2005-03-17
forum: General Help
---

### Post by h88 on 2005-03-17
Hey everyone,

I've had a wonderful opportunity of trying linux for the first time ever through the ubuntu distro. I tried it on my athlon desktop, and it works perfectly. However, on my centrino tablet/laptop, it fails to run the live cd.

The error was something about the failure of loading the GUI, and then I'm presented with a command line interface. Can someone spot the error and post the solution, please?

Thank you.

---

### Post by rmjokers on 2005-03-17
It is possible that the Ubuntu version you are using does not support the graphics card in your laptop.  Do you have any details about what kind of card you have?

---

### Post by alastair on 2005-03-17
Can't spot the error from over here, sorry ...

Maybe more information? e.g.

make/model of laptop
graphics chip
/var/log/Xorg.0.log (or /var/log/XF86Config on warty)
/etc/X11/xorg.conf (or /etc/X11/XF86Config on warty)

---

### Post by NuSYS on 2005-03-18
Try at boot this:
linux vga=771

---

### Post by h88 on 2005-03-20
Thanks alot guys - I ended up installing ubuntu on my laptop, but thanks for your help!

ubuntu rocks!

---

