---
title: "how to emulate a scrollwheel on a Logitech marble mouse in 10.04"
date: 2010-05-04
forum: General Help
---

### Post by drevicko on 2010-05-04
I've just upgraded to 10.04, and I want to set up my marble mouse to emulate a scroll wheel.

I found this: [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)
which tells how to set up udev rules and suggesting to use xorg.conf.d snippets. Unfortunately, neither is working..

attempting udev:
I've triggered the 'add' action with udevadm, rebooted...
I ran udevadm test, saw it find my 99_marblemouse.rules file, and execute some rules from other files. It didn't report anything about rules in my rules file, but maybe it doesn't report ENV{...}=... commands anyway.

attempting the xorg.conf way (which worked with 9.10) didn't seem to do anything..

Xorg.0.log reports some default settings when I plug it in, but not mine.

I can make it work with xinput set-int-prop ... commands - not pretty, but at least it's not driving me crazy (:
Ian

---

