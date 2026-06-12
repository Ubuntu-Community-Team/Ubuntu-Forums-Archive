---
title: "how could i have one pc with two indepent mice, kbs, screens?"
date: 2006-05-17
forum: General Help
---

### Post by bb002 on 2006-05-17
I have a pretty good Idea on how to do it just missing some of the finer details.

I'd have to setup a xorg.conf exactly like i want it and have it setup for one mouse, kb, screen. then copy it to xorg.2.conf and modify it to use the other mouse, kb, screen. Last i would have to edit /etc/init.d/gdm to start a second xserver and gdm login with the alternate xorg.conf.

I had a laptop that required three sections for the mouse (touchpad, tablet screen, and one for any external mice.) so i know how to split up the mice no problem. I know how to setup a xserver to use two screens, not two xservers and two screens. My concern is with two keyboards, i don't know if linux supports separating kb devices.

I found encouraging but old info at [http://cambuca.ldhs.cetuc.puc-rio.br/multiuser/](http://cambuca.ldhs.cetuc.puc-rio.br/multiuser/) that page looked like it did what i want to with one xserver/xorg.conf.


Anyone know of some example configs that use X.org?

also should i get this working how do i make it so users can't reboot/shutdown the machine. Currently the log off dialog has buttons for restart/shutdown. I would like to change this on a per user basis.

Thanks in advance for any help and/or tips.

---

