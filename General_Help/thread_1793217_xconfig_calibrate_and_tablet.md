---
title: "xconfig calibrate and tablet"
date: 2011-06-29
forum: General Help
---

### Post by thomasw81 on 2011-06-29
Hi Guys,

I got Ubuntu to work with a touchscreen (11.04 Gnome). One small issue remains: the X-axis is inverted. After calibrating with xconfig_calibrate it works fine, but after every reboot calibration has to be done again..

Any idea how to keep calibration settings perminantly?

Thanks for all answers!

Thomas

---

### Post by Favux on 2011-07-02
Hi thomasw81,

Sure you just put the calibration command with the coordinates you got from xinput-calibrator in a text file and name it what you want.  Then right click on it and in Properties in the Permission tab make it executable.  Then Add it into Startup Applications.

---

