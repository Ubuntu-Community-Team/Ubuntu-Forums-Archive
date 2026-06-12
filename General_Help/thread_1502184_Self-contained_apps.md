---
title: "Self-contained apps"
date: 2010-06-05
forum: General Help
---

### Post by Tomonomonous on 2010-06-05
Like on Mac OS X. It seems like a good idea, fairly user friendly and more organized but it seems to have died out in the Linux world. Is it a good idea or what?

---

### Post by HermanAB on 2010-06-05
Well, 
./configure 
make
make install

is easy enough...

---

### Post by dv3500ea on 2010-06-05
You mean the 'app folder'. The Debian package management system used in Ubuntu is far superior. It allows for a similar ease in adding/removing applications (through synaptic or another front end) but uses less disk space because applications can rely on one another and in turn can rely on a common set of packages. The Mac system requires all apps to bundle their required libraries, increasing the disk space used.

---

### Post by PauloStar on 2010-07-14
I think it's a great idea. It could probably be implemented using a Nautilus plugin.

You're unlikely to find much support from the community though. Hardcore Linux users tend to be very close minded to changes based on an influence from OSX or Windows. Just look at the massive opposition to the Gobo file system.

---

### Post by Penguin Guy on 2010-07-14
Should we have: [COLOR="Green"]manuals/applicationX[/COLOR] or [COLOR="green"]applicationX/manual[/COLOR]?

Using a hierarchy for files was one of the worst ideas in history.

---

### Post by Tomonomonous on 2010-07-15
It just so happens that this subject has started to recieve some more attention. :D

[http://www.omgubuntu.co.uk/2010/07/portable-linux-apps-run-your-favourite.html](http://www.omgubuntu.co.uk/2010/07/portable-linux-apps-run-your-favourite.html)

---

### Post by metalf8801 on 2010-07-16
This article explains how to turn .deb apps into portable single file apps 

[http://www.omgubuntu.co.uk/2010/07/distro-agnostic-packaging-making.html](http://www.omgubuntu.co.uk/2010/07/distro-agnostic-packaging-making.html)


This sounds great but I wonder how updates will be handled?

---

