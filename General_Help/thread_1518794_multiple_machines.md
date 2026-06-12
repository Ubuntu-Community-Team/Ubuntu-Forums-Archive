---
title: "multiple machines"
date: 2010-06-27
forum: General Help
---

### Post by mosaic2s on 2010-06-27
am using 10.04 and quite happy with the way it is working. my nephew and my mother have also switched to ubuntu.

to save on internet usage and load on the ubuntu servers, can i download upgrade files in one computer and then upgrade all systems?

---

### Post by dino99 on 2010-06-27
[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/)

[http://www.google.com/search?hl=fr&q=ubuntu%2Bshare%2Bfiles&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=fr&q=ubuntu%2Bshare%2Bfiles&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

### Post by coldraven on 2010-06-27
In Synaptic you can choose to downlioad the package files only.
See the checkbox in the screenshot.
I have not tried this, there is probably an easier way using the command line and apt.
It may not be so good for upgrades but would be handy for applications that you want on each machine.

---

### Post by gmargo on 2010-06-27
Your best bet is to install a "caching proxy server for Debian archive files" on one of your machines, and configure all of the machines to go through it.  Any .deb packages are then only downloaded once, on demand, and saved on disk for anyone else who needs it.

I use the **approx** package, other choices are **apt-cacher**, **apt-cacher-ng**, **apt-proxy**.

[http://packages.ubuntu.com/lucid/approx](http://packages.ubuntu.com/lucid/approx)
[http://packages.ubuntu.com/lucid/apt-cacher](http://packages.ubuntu.com/lucid/apt-cacher)
[http://packages.ubuntu.com/lucid/apt-cacher-ng](http://packages.ubuntu.com/lucid/apt-cacher-ng)
[http://packages.ubuntu.com/lucid/apt-proxy](http://packages.ubuntu.com/lucid/apt-proxy)

---

