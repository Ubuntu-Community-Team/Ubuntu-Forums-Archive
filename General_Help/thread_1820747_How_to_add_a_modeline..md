---
title: "How to add a modeline."
date: 2011-08-08
forum: General Help
---

### Post by Housemd on 2011-08-08
Hi,
Just install ubuntu but there is a problem of overscan.
It happened in the past too,I've found a way to solve the problem by adding this modeline:

"1920x1080_60.00" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync

My only question is,How?How can I add the modeline to xorg.conf?I tried to use sudo gedit /etc/X11/xorg.conf to do so but the file was empty and I didn't know where to start.
Can I add the modeline by the xrandr command?

Sorry for bad english and organization.

Thanks

---

### Post by dcstar on 2011-08-08
> **Housemd said:**
> Hi,
Just install ubuntu but there is a problem of overscan.
It happened in the past too,I've found a way to solve the problem by adding this modeline:

"1920x1080_60.00" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync

My only question is,How?How can I add the modeline to xorg.conf?I tried to use sudo gedit /etc/X11/xorg.conf to do so but the file was empty and I didn't know where to start.
Can I add the modeline by the xrandr command?

Sorry for bad english and organization.

Thanks

[https://www.linuxquestions.org/questions/linux-hardware-18/video-resolution-issue-for-ubuntu-10-04-a-809681/#post3979613](https://www.linuxquestions.org/questions/linux-hardware-18/video-resolution-issue-for-ubuntu-10-04-a-809681/#post3979613)

---

