---
title: "Xephyr will not span dual monitor in fullscreen"
date: 2012-07-19
forum: General Help
---

### Post by phatchow on 2012-07-19
First I would like to note that this is not multi-seat.

I am trying to set up Xephyr to run on a thin client (both Ubuntu 12.04 OS) and remotely connect to a machine that requires a dual monitor display for its application.  It also must be full screen to display the application correctly.

First I set up dual monitor with xrandr

>xrandr --output DVI-1 --mode 1280x1024 --output VGA-0 --mode 1280x1024 --above DVI-1

And all is well, then I attempt to run Xephyr...

>Xephyr :1 -query myhost -once -fullscreen -keybd ephyr,,,xkbmodel=uvdev

Xephyr only displays on the bottom display, the top display still shows my thin client desktop.

Any insights would be greatly appreciated!

---

