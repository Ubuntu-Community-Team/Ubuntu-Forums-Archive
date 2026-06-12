---
title: "How to edit application menu?"
date: 2011-08-09
forum: General Help
---

### Post by woodyg on 2011-08-09
I'm on Xubuntu 11.04. How do I add/remove items in the applications menu? I've tried lxmed, which was a piece of junk... the menu items it presented didn't even match the applications in my menu! Is there something better? GUI please...:)

---

### Post by mike555 on 2011-08-09
There is no gui made for xubuntu menu, you must edit .xml text files.... 


got this from xfce forum;

Add an applicatation to the menu:
You have to create a .desktop file (usually in /usr/share/applications/) for the app you want to add.

In the following example, we create a entry in the menu with the name "foo" in the submenu "Multimedia":

[Desktop Entry]
Encoding=UTF-8
Name=foo
GenericName=bar
Comment=Senseless programm ever
Exec=foobar
Icon=/usr/share/pixmaps/foobar.xpm
Terminal=false
Type=Application
Categories=Multimedia;



Remove an application to the menu:
You can do this in to ways.
First way, and the easier one is to simply remove the .desktop file in the /usr/share/applications/-folder.
The second way is, to add this line to the .desktop file:

NoDisplay=true
-----------------------------------------------------
( How to add or remove apps from the system's menu... (Page 1) / Frequently Asked Questions / Xfce Forums )
( Mon 01 Aug 2011 08:10:51 AM EDT )
( [http://forum.xfce.org/viewtopic.php?id=2658](http://forum.xfce.org/viewtopic.php?id=2658) )

---

### Post by woodyg on 2011-08-10
Cheers for that. :D Later came across [Xfce Wiki]("http://wiki.xfce.org/howto/customize-menu") which was outdated (pointing to wrong directories). More useful and updated info on how to edit the menu on [fedoraforum.org]("http://www.fedoraforum.org/forum/showthread.php?t=265583").

---

### Post by woodyg on 2011-10-28
ok, I did it all over again now after a fresh install of 11.10. The instructions still seem to work... but a proper menu editing tool (GUI) would still be nice. Has anyone seen such a thing?

---

### Post by Toz on 2011-10-28
> **woodyg said:**
> ok, I did it all over again now after a fresh install of 11.10. The instructions still seem to work... but a proper menu editing tool (GUI) would still be nice. Has anyone seen such a thing?

A menu editor is scheduled for version 4.10 - its called Garcon. See the roadmap: [http://wiki.xfce.org/releng/4.10/roadmap]("http://wiki.xfce.org/releng/4.10/roadmap").

---

### Post by woodyg on 2011-10-29
Great news :D

---

