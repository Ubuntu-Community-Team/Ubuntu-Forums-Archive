---
title: "Adjusting speed&amp;sensitivity of Trackpoint on T42?"
date: 2006-04-06
forum: General Help
---

### Post by bojaren on 2006-04-06
I consulted configure-trackpoint section of thinkwiki.org . There says that echoing some values like follows;
# echo -n 120 > /sys/devices/platform/i8042/serio0/serio2/speed 

it worked, but the effect lasts only that session.
After I reboot, the value I added returns to default. 

Is there any way to be fixed this speed&sensitivity setting permanently?

---

### Post by moephan on 2006-04-06
I'm far from an expert here, but I think the general approach is to edit /etc/X11/xorg.conf. Here's a link to a related thread:
[http://ubuntuforums.org/showthread.php?t=132590](http://ubuntuforums.org/showthread.php?t=132590)

Cheers, Rick

---

