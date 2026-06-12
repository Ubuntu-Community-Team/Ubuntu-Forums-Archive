---
title: "Firefox, windows won't resize, drop-downs broken"
date: 2011-08-07
forum: General Help
---

### Post by pifactory3142 on 2011-08-07
I'm running xubuntu 11.04 on an Asus eeepc with atom processor

I have a number of bugs with Firefox:

* Windows are a small fixed size of less than 6 inches wide by about 4 inches deep. I cannot resize by dragging the lower RH corner. The window can be moved around the screen.

* If I create a new window, it is the same size. Only the latest window can be used. It is not possible to click and switch between the windows.

* The drop-down menus either don't drop down, or if they do, it is not possible to choose an item.

I have fully removed Firefox using Synaptic and then reinstalled. The problem remains.

The machine is proving to be unstable, so there may be another cause. My latest issue was to have a "Kernel Panic"... I will post separately on that.

Any ideas? Missing Firefox plugins?

Thanks.

---

### Post by Toz on 2011-08-07
Perhaps the window manager has crashed and isn't running. Try pressing Alt+F2 and running the following command:
```
xfwm4 --display=:0.0 --replace
```

---

### Post by pifactory3142 on 2011-08-07
Thanks for your time and trouble.

Problem fixed.

Thanks again.

---

### Post by shiellb on 2011-09-05
Toz...you made my day.  Thank you.:popcorn:

---

