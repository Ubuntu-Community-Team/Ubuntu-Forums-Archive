---
title: "Display resolution 800x600"
date: 2010-07-30
forum: General Help
---

### Post by Merrr on 2010-07-30
Hi there,

since i've installed xubuntu it's running nice and smooth on my laptop. The display resolution is however set to 800x600 leaving a black bar at each side of the screen. I've searched a number of topics, but got stuck anyway. 
Is there anyone who knows how to solve this? 

Note: I can't find the xorg.conf file I know from other linux versions.

---

### Post by roger_1960 on 2010-07-30
Hi

By default there is no xorg.conf file, but if you create one it will be used.  If you have a copy of an old one which worked on a previous release, use that.  If not, we really need to know what graphics card you have to be able to help.  Please post the output from

> lspci

An empty file can be created using
> gksudo mousepad /etc/X11/xorg.conf

---

