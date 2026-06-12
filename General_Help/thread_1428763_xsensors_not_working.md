---
title: "xsensors not working"
date: 2010-03-13
forum: General Help
---

### Post by karmicgaz on 2010-03-13
Downloaded xsensors from repository but screen is just completely blank?

---

### Post by karmicgaz on 2010-03-13
sorry, should have said I just want some temperature monitoring software

---

### Post by Mark Phelps on 2010-03-13
Xsensors just provides a way to display the sensor values -- it does not install the sensor modules themselves.

To do that, you need to install lm-sensors.  Then, open a terminal and enter "sudo sensors-detect" and response with Y to every question, and allow it to install the sensor lines.

When you reboot, open a terminal and enter "sensors".  If you get a bunch of readings, the sensor modules are working.  If not, Xsensors will have nothing to read/display.

---

### Post by fragos on 2010-03-13
You can install the Gnome sensors applet and you can monitor your sensors in the top applet bar. Works well for me and it's display is very customizable.

---

