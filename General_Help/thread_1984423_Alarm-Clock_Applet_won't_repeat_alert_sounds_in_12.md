---
title: "Alarm-Clock Applet won't repeat alert sounds in 12.04"
date: 2012-05-21
forum: General Help
---

### Post by rewyllys on 2012-05-21
I've just installed Linux Mint 13RC, which is based on Ubuntu 12.04.  The  only problem I've found (so far -- knock on wood) is not with 13RC but  with an application in it: viz., Alarm-Clock-Applet, [http://alarm-clock.pseudoberries.com](http://alarm-clock.pseudoberries.com), which is available through Synaptic and the Software Center.

This  is an applet on which I depend heavily to manage my sessions at my  desktop.  It has worked perfectly for me in Linux Mint 11 (based on Ubuntu 11.04), but in LM13 the alert  sounds are played only once, whether or not I select the "Repeat sound"  option in the applet.   The difference is that LM11 uses v. 0.3.1 of the  applet, and LM13 uses version 0.3.2.

It turns out that this new  (and latest) version of Alarm-Clock-Applet has a bug in it: the failure  to repeat the alert sounds.  The bug is known to the developer, Johannes  Jensen. He has offered a work-around in [https://bugs.launchpad.net/ubuntu/+source/alarm-clock-applet/+bug/977110?comments=all](https://bugs.launchpad.net/ubuntu/+source/alarm-clock-applet/+bug/977110?comments=all)

The work-around involves changing the format of the alert sounds the user wants to use, from OGG to WAV.  However, the **names**  of the files must remain unchanged.  The files to be changed are  located in the following directory:   /usr/share/sounds/gnome/default/alerts/

---

