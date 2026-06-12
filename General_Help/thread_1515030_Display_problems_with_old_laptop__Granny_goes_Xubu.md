---
title: "Display problems with old laptop / Granny goes Xubuntu"
date: 2010-06-21
forum: General Help
---

### Post by Nr90 on 2010-06-21
Hi guys,
I am setting up my Grandma's laptop.
It's a very old laptop (although not as old as she is :lolflag:)
It's a Toshiba Satellite S1400-503 laptop.

It ran horribly under windows XP and neightbours and other relatives kept on installing stuff that slowed the system down even further. To stop that I installed Xubuntu 10.04 and so far it's running pretty good considering the age of this laptop.

One problem:
The display resolution won't go over 800x600 and it won't fill the entire screen (above and next to the screen are black bars of about 3 and 3,5 cm respectively). I searched the forum and found this to be a known problem with this laptop. There where solutions available at the time (during 8.04 and 7.10) that did seem to help. The problem is that the system has changed to much since then to use those solutions without more knowledge about coding/linux.

In conclusion, do you guys know any solutions that will let my grandma experience ubuntu full screen?:popcorn:

---

### Post by bobcollard on 2010-06-21
Just a suggestion, sometimes the resolution is correlated with the refresh rate.  Try 60hz if it is on 75hz.  If that is changed try to raise the resolution to 1024x768.  See if you can get a newer driver for the video board that is in the computer.  Hope one of these ideas help.

---

### Post by Nr90 on 2010-06-22
fixed it by creating a new xorg.conf file

---

