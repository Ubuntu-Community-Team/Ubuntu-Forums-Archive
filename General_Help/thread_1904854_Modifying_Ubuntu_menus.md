---
title: "Modifying Ubuntu menus"
date: 2012-01-05
forum: General Help
---

### Post by rmcellig on 2012-01-05
I am using Ubuntu 10.04 and love it! When I right click on the main menu in the upper left hand corner,and select Edit Menus, I would like to totally redo the menus to my liking. Seems pretty straight forward to me. My question is, if I do this, how will Ubuntu know where to install new software? The way it is now, Ubuntu knows that Avidemux belongs under Sound & Video, Abiword belongs under the Office menu. Are there serious issues if I decide to rearrange/ rename menu items?

---

### Post by cogier on 2012-01-05
I think you will find that Ubuntu has a fixed place to display the item on a menu. If you therefore remove a menu heading Ubuntu will simply recreate it and put the new piece of software where it has been instructed to. 

If you install Gambas and you do not have a "Programming" menu option Ubuntu just creates it.

The only issue being that you will end up moving things around each time you add a new piece of software.

---

### Post by Mark Phelps on 2012-01-05
The app installation, if it adds a menu entry, is coded already for that entry; thus as already said, if you remove the parent menu entry and install an app that uses it, that app will simply recreate the partent menu entry.

Don't get too used to this, though, as the whole menu entry concept is sunsetting with the continued push toward the Unity desktop.

---

### Post by bab1 on 2012-01-05
> **rmcellig said:**
> I am using Ubuntu 10.04 and love it! When I right click on the main menu in the upper left hand corner,and select Edit Menus, I would like to totally redo the menus to my liking. Seems pretty straight forward to me. My question is, if I do this, how will Ubuntu know where to install new software? The way it is now, Ubuntu knows that Avidemux belongs under Sound & Video, Abiword belongs under the Office menu. Are there serious issues if I decide to rearrange/ rename menu items?

Those are shortcuts to the executable application.  You can certainly can create custom  menus. I have a menu for the apps I use the most and all the default menus too.  You can have duplicates on multiple menus.

Ubuntu adds items to the menus based on the directions in the .deb file (at installation), but your shortcuts are not restricted as to how many or where they are located.

---

