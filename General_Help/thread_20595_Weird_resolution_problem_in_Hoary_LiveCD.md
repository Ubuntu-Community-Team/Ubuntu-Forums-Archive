---
title: "Weird resolution problem in Hoary LiveCD"
date: 2005-03-17
forum: General Help
---

### Post by slysy81 on 2005-03-17
I would be very grateful if someone could help with this. I have an ATI x800xt graphics card. When I boot the Hoary LiveCD I am having a problem with the resoultion. I am running in 1280 x 1024, but I cannot see the whole desktop at once. Instead I see the tope left quarter of the screen. If I move the mouse to the right or bottom, the screen scrolls in that direction to show another part of the desktop. I have no problems in 640 x 480.

How can I make the desktop display properly an fully without scrolling? Maybe there is a parameter I can use when booting?

Many thanks for any help,

slysy81

---

### Post by alastair on 2005-03-17
It looks like a "virtual desktop" problem. What is in the Xorg config file?

/etc/X11/xorg.conf

Any mention of "virtual"?

---

