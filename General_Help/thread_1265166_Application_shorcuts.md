---
title: "Application shorcuts"
date: 2009-09-13
forum: General Help
---

### Post by anupam sadhukhan on 2009-09-13
Can anybody tell me how to move one application from one category to another for example move an application from "Sound and Video" to "Office" category. Is there any way of creating/modifying application categories that is shown in GNOME main menu.

---

### Post by ad_267 on 2009-09-13
Right click on the menu button and select edit menus. Or go to System - Preferences - Menu.

---

### Post by kerry_s on 2009-09-13
> **ad_267 said:**
> Right click on the menu button and select edit menus. Or go to System - Preferences - Menu.

you forgot to say how. :lolflag:
anyways, once your in the menu editor, the stuff is drag & drop able, so you can put it where ever you want.

---

### Post by mc4man on 2009-09-13
The way they got into the menu in a specific place is how you can move them.
( though for the most part they're where they belong.

More useful for creating new items, or slightly different versions (launch commands of same apps. In those cases the .desktops would be in your home and a little easier and more appropriate to edit.

Anyway an ex.

Moving grip from Sound & Video to office.

The grip.desktop is in /usr/share/applications and has to be edited by root.

Orig. grip desktop

> Name=Grip
[COLOR="Red"]clipped[/COLOR]
Exec=grip
Icon=gripicon.png
Type=Application
Categories=Application;[COLOR="Blue"]AudioVideo;[/COLOR]

Edited to be in office
> Name=Grip
[COLOR="Red"]clipped[/COLOR]
Exec=grip
Icon=gripicon.png
Type=Application
Categories=Application[COLOR="Blue"];Office;[/COLOR]


After retarting x it will be found in applications  -> office

As mentioned I's prefer to do such things in ~/.local/share/applications

---

### Post by kerry_s on 2009-09-13
> **mc4man said:**
> The way they got into the menu in a specific place is how you can move them.
( though for the most part they're where they belong.

More useful for creating new items, or slightly different versions (launch commands of same apps. In those cases the .desktops would be in your home and a little easier and more appropriate to edit.

Anyway an ex.

Moving grip from Sound & Video to office.

The grip.desktop is in /usr/share/applications and has to be edited by root.

Orig. grip desktop



Edited to be in office


After retarting x it will be found in applications  -> office

As mentioned I's prefer to do such things in ~/.local/share/applications


just a reminder, that will have to be done every time that program is upgraded.

---

### Post by anupam sadhukhan on 2009-09-13
Thanks to everybody for the help. It was my first post in ubuntu forum and I got such a quick reply.

---

