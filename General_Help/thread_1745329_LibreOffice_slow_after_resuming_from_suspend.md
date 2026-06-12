---
title: "LibreOffice slow after resuming from suspend"
date: 2011-04-30
forum: General Help
---

### Post by Ben Kuhn on 2011-04-30
Hi,

LibreOffice usually works fine for me, but after I suspend and resume my machine, it suddenly takes ages to page up/down, focus the window, or some other things (editing text is a little laggy, but doable). After restarting the program everything works fine again. Any idea what's going on?

Not really sure what troubleshooting info would be relevant here, but I'm on Natty, all packages up-to-date as of 4/30, and my computer is an Asus K61IC (Nvidia discrete graphics, proprietary driver version "current").

Thanks!

---

### Post by aldeby on 2011-05-08
I can confirm this behavior happens to me too when the following conditions are met:
- nvidia propietary drivers
- libreoffice 3.3.2
- resume after suspend

haven't found a solution yet.

---

### Post by learst on 2011-05-12
Have the same problem.

Running on Ubuntu 10.10, nVidia proprietary drivers, and Libreoffice 3.3.2.

I think this is a carryover bug from OpenOffice, as I experienced the same thing when using OO 3.3 before switching to LibreOffice.

---

### Post by blueidealist on 2011-05-31
I confirm the strange behavior with
Ubuntu 11.04
Nvidia acceleration with appropriate drivers
LibreOffice 3.3.2 - except LibreOffice can slow my computer down to such an amount that it can go to a complete freeze.

---

### Post by V|r on 2011-06-29
I also have this problem. While LibreOffice is a very serious case, this also happens for the rest of the desktop.

Sometimes I see the Xorg process going to 100% CPU usage, burning one core. SDL games that draw the mouse cursor (OpenTTD, Wesnoth - where it can be disabled) become completely unusable.

I tried many things, and the best fix has always been to use the Nvidia driver with versions below 200. But since Natty those don't compile anymore.

---

### Post by wastvedt on 2011-08-21
Has anyone found a solution to this problem? I have the same issue, with Ubuntu 11.04 64 bit, Nvidia driver: 270.41.06, kernel 2.6.38-8 generic, Libre Office 3.3.3.

Trygve

---

