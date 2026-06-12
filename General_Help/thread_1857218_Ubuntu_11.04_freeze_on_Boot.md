---
title: "Ubuntu 11.04 freeze on Boot"
date: 2011-10-09
forum: General Help
---

### Post by sunasia on 2011-10-09
I switched on my  Dell Inspiron m4010 notebook after a week not using and when my ubuntu 11.04 OS boots I get my homescreen with the little white circle on screen which would normally convert to the mouse/touchpad pointer, but it doesnt . So I am stuck and can't move any further , I have re booted many times but no luck. Is there any way to solve this other than a re install? Appreciate some help . Thanks
If I go in recovery start up what do I Do when I get this menu
I have these options.

Resume
Clean
dpkg- repair broken packages
failsafex- run in failsafe graphic mode
fsck- reboot into file system check
grub- update grub bootloader
netroot- drop to rootshell prompt with networking
root- drop to rootshell prompt

what do I select and do next , Thanks

---

### Post by TeoBigusGeekus on 2011-10-10
Choose netroot and once on command line try these commands:
```
apt-get update
apt-get upgrade
```

---

