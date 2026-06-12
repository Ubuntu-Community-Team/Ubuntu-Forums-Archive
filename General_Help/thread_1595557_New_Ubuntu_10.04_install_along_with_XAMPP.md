---
title: "New Ubuntu 10.04 install along with XAMPP"
date: 2010-10-13
forum: General Help
---

### Post by PBWall on 2010-10-13
I am a new user to the linux world. I am trying to put together a working configuration of Ubuntu 10.04 with XAMPP 1.7.1. (final goal is working kalturaCE application).
 
Anyway, I've gone through all the installation guidelines that I could find and was able to get ubuntu installed (very easy) along with the other two apps. 
 
I can successfully browse to the kaltura app from the local network but I cannot get to it from the outside world (cannot get to kaltura or the base XAMPP file)? Is there a configuration where I could have possibly only told apache to respond to localhost and local lan?
 
Thank you.

---

### Post by Refalm on 2010-10-13
Installing XAMPP on Linux is generally a bad idea in the first place (no security updates, manually insert modules like ImageMagick, being laughed at by the cool Linux kids, etc.).
I suggest you remove it.

It's a better idea to get [Ubuntu Server]("http://www.ubuntu.com/server"), and then select "LAMP" at the installation.

Or if you want to keep your current install, follow this tutorial:
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

