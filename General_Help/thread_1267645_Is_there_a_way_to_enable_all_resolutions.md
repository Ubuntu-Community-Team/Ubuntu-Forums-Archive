---
title: "Is there a way to enable all resolutions?"
date: 2009-09-16
forum: General Help
---

### Post by amrasurion on 2009-09-16
this is what is confusing me, when i do gksudo nvidia-settings i can put w.e resolution i want in. Now, i know this monitor can do 1600x1200 but when i make that the value, it refreshes and i have to use my mouse to scroll around and be able to see the bottom of the screen. I'm assuming there's some wierd problem here since it never did that before and I used to use 1600x1200 res on other releases up untill 9.04.

if it matters my gpu is nvidia 8600 GTS Thank you and i'll be checking back shortly.

---

### Post by amrasurion on 2009-09-16
bump?

---

### Post by amrasurion on 2009-09-16
bump again..

---

### Post by P4man on 2009-09-16
Please don't bump every hour, you're not holding the line on a commercial phone support ;)

You probably have a 1600x1200 virtual desktop configured in your xorg.conf, and for some reason it boots in a different, lower resolution which gives you that scrolling thing. 

If you change the settings in nvidia-setting, did you save it to your xorg.conf file (called X configuration in the nvidia applet) ?

If so, please post the contents of /etc/X11/xorg.conf

---

