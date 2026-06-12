---
title: "Package install kills gnome"
date: 2006-04-19
forum: General Help
---

### Post by moratis on 2006-04-19
I don't have an internet connection for my laptop at work so I have been using a thumb drive to swap packages back and forth, desktop to laptop.  I have been trying install an mp3 decoder ( gstreamer0.8 ), but executing

~# sudo dpkg -i gstreamer0.8-......deb

was unsuccessful as gstreamer depends on other outdated packages:

libglib2.0-0
libid3tag0
libmad0
libxml2

I installed those packages with dpkg.  Immeadiately afterwards, any application I tried to run failed.  After a reboot, GNOME failed to load.  I entered into a failsafe terminal and removed libid3tag0 and libmad0, but the other two had dependency issues and couldn't be removed.  How can I fix GNOME, or replace the remaining packages with their older versions?  Remember I have no internet access on the linux box.  Thanks!

---

