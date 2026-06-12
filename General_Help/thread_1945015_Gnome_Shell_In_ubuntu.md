---
title: "Gnome Shell In ubuntu"
date: 2012-03-22
forum: General Help
---

### Post by holytree on 2012-03-22
HI i am running ubuntu 12.04 beta 
dont shift to +1 forum as this is a general question

I want to create shortcuts of chromium ,Software center on my desktop but the names are annoyingly long.

any help pls?

regards,
holytree

---

### Post by kurt18947 on 2012-03-22
Gnome shell desktop launchers can be created though it's a terminal operation AFAIK.  Try this:
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```This should open 'create launcher' dialog box where you enter the name and command for your app.

---

### Post by ajgreeny on 2012-03-22
If you open, for example, the chromium or scribus.desktop file using gedit you will find that most of the text in the shortcut on your desktop is not its name but the "comment" which you can edit as you wish, or remove.  I don't know gnome-3 but maybe you can right click on the shortcut, choose Properties, and you may be able to do exactly the same with the gui.

---

