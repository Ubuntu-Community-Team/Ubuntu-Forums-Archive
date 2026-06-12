---
title: "Location of panels, custom menus, colors ++++"
date: 2009-09-14
forum: General Help
---

### Post by measekite on 2009-09-14
I know that these items are in hidden files somewhere in /username.

What I would like to know is both the name of the folder and the name or names of the files.  I would also like to know if you can view them in a text editor.

Where can I find the name and location of every configuration file and how to interpret and understand their functions?

---

### Post by ajgreeny on 2009-09-14
A lot of what you want is in the **.gconf** folder in your home.  It is not quite that simple, however, and even though you could see all that in a text file, it would be difficult to edit that way unless you know all about xml coding.

The easiest way to do things with that folder is to open the **gconf-editor** either by typing exactly that in the Alt+F2 dialog box, or by unhiding the menu item for it, which you can do by right clicking the menu and choosing "Edit Menu".  I think it is in System Tools, but just search for it and select the tick box to make it show in the menu.

Backup the current .gconf folder with ```
cp -r /home/username/.gconf/ /home/username/.gconfbak/
``` before you do make any changes, just in case you mess things up too much, and then play around to your heart's content safe in the knowledge that you can get everything back if it all goes wrong

---

### Post by measekite on 2009-09-14
> **ajgreeny said:**
> A lot of what you want is in the **.gconf** folder in your home.  It is not quite that simple, however, and even though you could see all that in a text file, it would be difficult to edit that way unless you know all about xml coding.

The easiest way to do things with that folder is to open the **gconf-editor** either by typing exactly that in the Alt+F2 dialog box, or by unhiding the menu item for it, which you can do by right clicking the menu and choosing "Edit Menu".  I think it is in System Tools, but just search for it and select the tick box to make it show in the menu.

Backup the current .gconf folder with ```
cp -r /home/username/.gconf/ /home/username/.gconfbak/
``` before you do make any changes, just in case you mess things up too much, and then play around to your heart's content safe in the knowledge that you can get everything back if it all goes wrong

Thanks

---

