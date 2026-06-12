---
title: "Compositing issues"
date: 2010-08-27
forum: General Help
---

### Post by sr.vinay on 2010-08-27
The compositing option is set to off by default. When I installed the OS though, it used to be on by default. I checked KDE's page and tried a few commands they've put up, but in vain. I've to press Alt+Shift+F12 each time I log in, to make it work. It works fine; there are no issues with my graphics card.
I just want to turn it on by default.

---

### Post by ankspo71 on 2010-08-28
Hi,
It could be a problem in the kwinrc file. It is located at:
/home/yourname/.kde/share/config/kwinrc

These kde forum posts might be of some help.
[http://forum.kde.org/viewtopic.php?f=66&t=19956](http://forum.kde.org/viewtopic.php?f=66&t=19956)
[http://forum.kde.org/viewtopic.php?f=17&t=6712](http://forum.kde.org/viewtopic.php?f=17&t=6712)
The plasmoids they mentioned might be worth a look too.

Also try going to System settings -> Desktop -> Advanced -> Disable functionality checks. This might stop turning off compositing at startup.

---

