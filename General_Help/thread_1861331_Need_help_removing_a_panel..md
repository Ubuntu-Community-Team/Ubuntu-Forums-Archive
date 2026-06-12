---
title: "Need help removing a panel."
date: 2011-10-15
forum: General Help
---

### Post by spiritech on 2011-10-15
HI
 
i have upgraded to Ubuntu 11.10. i have selected Cairo-dock ( gnome with  affects ) from the settings menu at the login screen. everything is  running OK, however i would like to remove the panel that is at the top  of the screen. it has the following options:- file, edit, view, go,  bookmarks, help.

---

### Post by spiritech on 2011-10-15
after some research i have discovered the following.

the panel i was referring to in this post is known as the Global Menu. i believe it is part of the Unity package. it is quite simple to remove by removing the following three packages-

appmenu-gtk3
appmenu-gtk
appmenu-qt

you can find these packages in your synaptic or in your Ubuntu Software center.

or alternatively you can run

sudo apt-get remove [FONT=Verdana]appmenu-gtk3 appmenu-gtk appmenu-qt

hope this helped. :)
[/FONT]

---

