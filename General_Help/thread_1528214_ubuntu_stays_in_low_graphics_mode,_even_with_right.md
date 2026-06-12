---
title: "ubuntu stays in low graphics mode, even with right driver??"
date: 2010-07-10
forum: General Help
---

### Post by killer62491 on 2010-07-10
hey all, im wondering how would one make ubuntu automatically start in "some graphics" mode on the desktop? for some reason, my laptop is always in an inverted colorscheme, and the only fix i can do is to use the invert colors function of the desktop. but this function is only available in any graphics mode higher than "low graphics" mode. for some reason, whenever i reboot the machine using the actual power button, rather than the System-> Shut Down... option, it will say it encountered an error when it reboots, before even showing the login screen. apparently the issue is due to the machine not loading the right driver as default, even though it is installed. how would i change the configuration of the system so it would automatically load the current driver as if it were the default?

---

### Post by dino99 on 2010-07-10
which ubuntu release are you talking about, which graphic card, which video driver installed and activated ?

into a console:

sudo rm -f /etc/X11/xorg.conf

then reboot and check: system admin hardware driver

---

