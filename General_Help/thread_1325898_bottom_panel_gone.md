---
title: "bottom panel gone"
date: 2009-11-13
forum: General Help
---

### Post by JimHebert on 2009-11-13
I'm new to Ubuntu and lost the bottom panel with the list of open windows. I searched the help section but so much info and don't know where to turn. Can't find how to  default it.

---

### Post by J-Buntu on 2009-11-13
Right click the top bar - select add to panel, select windows list.

---

### Post by skatinjj on 2009-11-13
You can right click the top panel and select new panel from the menu that appears.

Then right click the new panel and selet add to panel then find the window list applet for the panel.

---

### Post by JimHebert on 2009-11-14
I don't see anything that says add to panel or new panel. I right click on the panel that has Applications, Places, etc and I see Help, edit menus,remove from panel, move, and lock panel. I'm using Ubuntu 8.10, if that helps you.

---

### Post by JimHebert on 2009-11-14
No problem,  I've got it restored. Here is what you have to do, in case it should happen to you. Enter the following

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

---

### Post by J-Buntu on 2009-11-14
> **JimHebert said:**
> I don't see anything that says add to panel or new panel. I right click on the panel that has Applications, Places, etc and I see Help, edit menus,remove from panel, move, and lock panel. I'm using Ubuntu 8.10, if that helps you.
______________________

Maybe i didn't make it clear, but you had to right click on an empty area in the panel. It seems you were right clicking on the applets, therefore bringing up the "applets menu" - and not the "panel menu". If you click on an empty area of the panel, you will see the options "Add to Panel" and "New Panel". 

Glad you sorted your problem though anyway.

---

