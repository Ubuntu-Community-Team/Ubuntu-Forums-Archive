---
title: "Default settings guest user"
date: 2012-04-26
forum: General Help
---

### Post by javi_m on 2012-04-26
Hi everyone!

This is in no way a big deal, but i want some information about it.

It is possible to save settings in guest account? i'm with ubuntu 12.04, and want to have smaller icons on dash, some others icons (like Faenza) and so on. But obviously, if i change this properties inside the guest account, when loggging out it's all lost. Is there a way to save that seetings? so when i log in into guest account, all of these settings are loaded besides the default ones on the fresh installation.

Cheers!

---

### Post by Veltaz Crow on 2012-06-17
Hi,

You have to copy some files in the directory /etc/skel.

For example :
I am under Xubuntu, and for themes, I have to copy :
    ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml 
    ~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml
in the "skel" directory.

Make sure you copy all the informations needed, for example, for the xfce-panel I have to copy    ~/.config/xfce4/xfconf/xfce-perchannel-xml/panel.xml   and all the directories in     ~/.config/xfce4/panel/.

I hope that will help you !

Vel'

---

