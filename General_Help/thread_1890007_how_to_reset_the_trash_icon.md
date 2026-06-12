---
title: "how to reset the trash icon"
date: 2011-12-02
forum: General Help
---

### Post by agrayray on 2011-12-02
anyone know of the command to reset the lower panel bar or specifically reset my trash icon?  I hooked my laptop up to a projector which changed the screen resolution and now even in normal display my trash icon is in the middle versus at the end where Id like it.

Thanks in advance!

PS - Using 10.10 gnome desktop.

---

### Post by JRV on 2011-12-02
Right click on it, uncheck "Lock To Panel".
Right click on it, click on "Move" and put it where you want it.
Right click on it, check "Lock To Panel".

---

### Post by agrayray on 2011-12-02
thanks for the reply...but there is there is NO unlock option via right click...all i get it is:

Add to Panel
Properties
Delete This Panel
New Panel
Help
About Panels

and there is nothing in Properties either that seems to do the trick...I tried changing the expand and botton to left etc...options but when i set it back to bottom the trash icon shows up in the middle and i can not drag it....

i ended up with this:

gconftool --recursive-unset /apps/panel && killall gnome-panel

which resets all the panels and kinda a pain because it resets the top panel too...but couldnt find a way to reset just the bottom..if anyone knows for future would be grateful.

---

### Post by JRV on 2011-12-02
Right click on the trash can.

---

