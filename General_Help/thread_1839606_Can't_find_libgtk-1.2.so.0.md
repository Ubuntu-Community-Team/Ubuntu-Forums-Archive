---
title: "Can't find libgtk-1.2.so.0"
date: 2011-09-05
forum: General Help
---

### Post by His Royal Freshness on 2011-09-05
I found [this thread]("http://ubuntuforums.org/showthread.php?t=920791") and tried all of the suggestions there, but no bones.  Synaptic gave me libgtk3.0, and I have no idea.  wat do.

---

### Post by mc4man on 2011-09-06
The last release to have those libs was jaunty which is EOL. You could probably find the packages needed in the old-release repo  to manually dl & install

A bit more accessible are the hardy versions which are still in launchpad
You'd want 2 gtk & 1 glib package, if desired after installing you could install the 2 respective -dev packages.

gtk from here, pick your arch from Builds group on the r. side
[https://launchpad.net/ubuntu/+source/gtk+1.2/1.2.10-18.1build2](https://launchpad.net/ubuntu/+source/gtk+1.2/1.2.10-18.1build2) 
libgtk1.2_common... (install 1st
libgtk1.2_1.2.10-18....deb (install 3rd

glib
[https://launchpad.net/ubuntu/+source/glib1.2/1.2.10-19build1](https://launchpad.net/ubuntu/+source/glib1.2/1.2.10-19build1)
libglib1.2ldbl (install 2nd

---

