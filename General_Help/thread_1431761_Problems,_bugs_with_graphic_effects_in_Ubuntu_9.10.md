---
title: "Problems, bugs with graphic effects in Ubuntu 9.10"
date: 2010-03-17
forum: General Help
---

### Post by chimi_12 on 2010-03-17
I installed ubuntu 9.10 at my home PC, it  all was working well (referring to graphic effects and video card). But  a few days ago were disabled the graphic effects of compizconfig .. No hub, not  the 4 desktops I had configured and all the nice effects of menus and  others who have ubuntu, are not now .. I do not understand what happened, the last  thing relevant was the installation of Google Earth but no idea if I'll  have to do something, try reinstalling the Nvidia driver (my card is a  GeForce 7200 GS) that you downloaded from Nvidia's website, which worked  perfect until a  couple of days, but on entering console (CTRL + ALT + F1) type the  following to disable xserver ..

sudo killall gdm

 or

sudo / etc / init.d / gdm stop

but in the first case he says that is  not the process or something and I pulled a few mistakes, however does  not stop the xserver so I can not reinstall the video driver ..
Just do not have graphic  acceleration but the dirver is properly installed

Not to do, not who is .. I would appreciate very much help to go back to have my ubuntu  and brag about their effects.

Thanks in advance

---

### Post by soltanis on 2010-03-17
Go to Applications->System->Hardware Drivers and tell me if the nVidia driver is enabled.

If not, enable it.

Compiz (the compositor) has a well established reputation for working one day and breaking the next for absolutely no reason, kind of like ALSA and NetworkManager.

---

### Post by chimi_12 on 2010-03-18
[COLOR=#000000][FONT=Times New Roman][FONT=Arial]Well, I checked and the driver is enabled, initially had used the NVidia dirver delivering from their website, when this happened, I tried enabling the driver provided by Ubuntu but still not working


[/FONT][/FONT][/COLOR]

---

