---
title: "Hangs at libglx"
date: 2009-06-28
forum: General Help
---

### Post by greenjambi on 2009-06-28
I am not able to install nvidia driver properly since when I moved to ubuntu 9.04

This is what I did :
System > Administration > Hardware drivers > version 180 
apt-get install nvidia-glx-180 
reboot

I get a blank screen. The system just hangs.
I try to reboot in to 'safe mode' , go bash 
and the /var/log/Xorg.0.log says ..

WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so


I did a lot of searching, but I dont see anyone else getting such an error. 

Can someone tell me where I am going wrong ?

---

### Post by greenjambi on 2009-06-30
bump

---

