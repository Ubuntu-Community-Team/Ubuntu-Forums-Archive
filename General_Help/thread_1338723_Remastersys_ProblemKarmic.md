---
title: "Remastersys Problem:Karmic"
date: 2009-11-26
forum: General Help
---

### Post by loneowais on 2009-11-26
I'm trying to remaster my Ubuntu but I'm experiencing the following problems.

1>
Most of the apps are automatically started on Live CD.
I tried deleting entries from /etc/xdg/autostart but it doesn't help.
These apps don't autostart on my regular install but do on the remastered disk.


2>
Themes don't work.I copied my custom themes to /usr/share/themes and they work fine on my regular install but are reported as Theme Not Installed on the remastered disk.

These issues never happened with previous versions of Ubuntu/Remastersys.

Please help.
We have a Linux Meet coming in a week and we want to distribute a copy of Ubuntu with all the codecs and extra apps. This is very important.

---

### Post by Kendall_Tristan on 2009-11-27
Have you had any install problems?  I'm using remastersys to do a Fluxbox Mint build so I haven't run into the degree of problems that you're facing, but the installer crashes everytime it gets to configuring Grub (~95%).

Regarding your problems, I had to do a lot of file system digging when I wanted certain apps to load on startup and I had to set them in a couple of places.  For me it was in /etc/skel and /usr/lib/linuxmint/etc/skel and both configurations had to be identical, so I'm thinking that there's something else somewhere before it'll end up on the live disk, but I could be wrong.

---

