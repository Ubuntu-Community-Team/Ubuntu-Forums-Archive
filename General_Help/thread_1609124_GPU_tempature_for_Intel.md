---
title: "GPU tempature for Intel?"
date: 2010-10-30
forum: General Help
---

### Post by eival on 2010-10-30
im using the proprietary driver in 10.4 since Intel doesnt have official Linux drivers, but i dont see any control panel similar to the one Nvidia has for linux that shows my internal temp as well as other graphical settings, is there a terminal code i have to use to unlock/install that? or is there another app i can download that will show me the GPU temp?

edit- i checked the software center and it says "intel-gpu-tools" is already installed, how do i run it? if i type it in the terminal it just brings up a blank text page.

---

### Post by P4man on 2010-10-30
First of all, there are no proprietary drivers for intel gpu's. There are only opensource kernel drivers. Only ATI and nVidia provide optional closed source proprietary videodrivers.

Next, intel-gpu-tools seems to be a package for debugging videdrivers, its not what you are looking for.

I dont have an intel system to test with at the moment, but in so far there is a thermal sensor in the gpu, I suspect you can read it with lm-sensors. Install *lm-sensors *and *sensors-applet*. Then in a terminal run

sudo sensors-detect

Follow the instructions, and select Y on every question. When its done, reboot and add sensor-applet to your panel and configure it, or check in the terminal with "sensors".

---

### Post by eival on 2010-10-30
thanks that worked.:popcorn:

---

