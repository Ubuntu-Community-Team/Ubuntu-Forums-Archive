---
title: "Sound Preferences Package Name"
date: 2012-01-19
forum: General Help
---

### Post by jmadero on 2012-01-19
Hi All,

Just looking for the package(s) name of the GUI frontend for pulse in ubuntu 11.10. The image looks like this:

[IMG]http://somethingkindawierd.com/blog/wp-content/uploads/2010/10/Selection_004.png[/IMG]


Thanks

---

### Post by dcstar on 2012-01-20
> **jmadero said:**
> Hi All,

Just looking for the package(s) name of the GUI frontend for pulse in ubuntu 11.10. The image looks like this:
.........

**gnome-volume-control** used to be part of the **gnome-media** package, I don't know if that still applies to your release.

---

### Post by xyzzyman on 2012-01-20
The one pictured is part of gnome-control-center now. 

If you're looking for one more pulse specific then pavucontrol gives you pulse audio control, which allows you to really get in and adjust things (Not as much with individual channel volume settings, but you can change recording sources better, etc. For example it's the only one that allows me to switch audio recorder to the built in monitor and record everything being played to my speakers.)

---

### Post by jmadero on 2012-01-23
Thanks to both of you, going to try installing gnome-control-center tonight on Bodhi, just think it's the most intuitive way to control Pulse. I do have pulse audio control but still lacks all the options and intuitive setup that the one that is part of Ubuntu 11.10 has. Unfortunately with so many other bugs in ubuntu 11.10 I'm having to move to another distro and want to get the same functionality that I used to have in Ubuntu. Thanks again



Edit: Any way to narrow down the package? looks like gnome-control-center is just a meta package which has a ton of related packages that get installed. Thanks again

---

