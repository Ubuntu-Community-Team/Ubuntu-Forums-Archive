---
title: "Edit Menus location in home folder"
date: 2010-11-04
forum: General Help
---

### Post by BobSongs on 2010-11-04
Okay, real quick help on editing the Ubuntu menus.

If I add a new item (launcher) to the main menu, where does it store this info in my home folder?

---

### Post by garvinrick4 on 2010-11-04
> **BobSongs said:**
> Okay, real quick help on editing the Ubuntu menus.

If I add a new item (launcher) to the main menu, where does it store this info in my home folder? You mean where is it in file system?
which (package name)
rick@rick-laptop:~$ which firefox
/usr/bin/firefox
Follow the path.

---

### Post by sikander3786 on 2010-11-04
I think what you are looking for is Menu folder under the hidden .config folder in home directory.

---

### Post by yetiman64 on 2010-11-04
> **BobSongs said:**
> Okay, real quick help on editing the Ubuntu menus.

If I add a new item (launcher) to the main menu, where does it store this info in my home folder?

The new launcher (*.desktop file) is stored in ~/.local/share/applications, where ~ represents your home folder.

Edit: if you use Wine, its folder for launchers and submenus will be in here as well in a folder named "Wine". Also as silkander3786 notes there is a ~/.config/menus folder which alacarte uses to store info for the creation/alteration of the menus themselves.

---

### Post by BobSongs on 2010-11-04
Fantastic!

I've been meaning to clean up this area as A La Carte seems to make a few mistakes from time to time.

Thank you, gentlemen. You are all scholars.

---

### Post by BobSongs on 2010-11-04
[COLOR=#333333]In particular: If I manually remove an entry from, say, Wine, then re-install the application, the Wine menu won't have the application icons from the most recent install.

Does anyone else get this too?[/COLOR]

---

### Post by sikander3786 on 2010-11-05
> **BobSongs said:**
> [COLOR=#333333]In particular: If I manually remove an entry from, say, Wine, then re-install the application, the Wine menu won't have the application icons from the most recent install.

Does anyone else get this too?[/COLOR]
I don't remember anything like that happening to me.

Most of the time, when I un-install an application, the shortcuts don't go away so I have to manually remove them from .wine directory. But, whenever I reinstall the same application, it automatically generates new shortcuts and icons.

Don't know why it doesn't act the same on your install.

---

