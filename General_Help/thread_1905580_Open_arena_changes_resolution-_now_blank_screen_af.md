---
title: "Open arena changes resolution- now blank screen after boot"
date: 2012-01-07
forum: General Help
---

### Post by i8bugs on 2012-01-07
Ubuntu 11.10/ Lenovo B570 Laptop
After installing Open Arena, the game permanently changed my resolution (to what I don't know).  When I boot to Ubuntu, I can get a login screen just fine, but after logging in, the screen goes blank.
I'm using Windows boot manager so I don't see grub.  I can login as a guest and get Ubuntu, but how can I fix my resolution on a guest login?  I don't want to have to do a reinstall.

---

### Post by i8bugs on 2012-01-08
Bump please.

---

### Post by alastair_hm on 2013-01-30
I had the same issue yesterday, Open Arena reset the resolution to  640x480 too small to see all the display properties setup window.

Found this link [http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

Which says;

"If you set a resolution inappropriate for your monitor in the Screen Resolution GUI tool, you can reset it by running rm ~/.config/monitors.xml from a terminal."

Also you could try to run this command to list your monitor and resolutions available

xrandr

Then run something like this to reset it;

xrandr --output VGA1 --mode 1024x768

---

