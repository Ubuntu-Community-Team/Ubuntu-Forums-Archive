---
title: "Help"
date: 2011-04-02
forum: General Help
---

### Post by Dexdrex007 on 2011-04-02
Hey guys, im a new user in ubuntu and im just starting to use it, so far im liking it.

my problem is if i right click the application , places system part. i only get Help. no edit menus or etc. i can't right click the programs inside application so i can create a shortcut either.

this is really bothering me.

Help is really appreciated thanks.

---

### Post by nothingspecial on 2011-04-02
Try going system > preferences > main menu

---

### Post by Dexdrex007 on 2011-04-02
still i can't right click the applications inside.

example: 

i'll right click the firefox browser, instead of showing a submenu, the program opens, i can't also drag them into the desktop.

---

### Post by Dexdrex007 on 2011-04-02
still i can't right click the applications inside.

example: 

i'll right click the firefox browser, instead of showing a submenu, the program opens, i can't also drag them into the desktop.

---

### Post by Dexdrex007 on 2011-04-02
help guys.

---

### Post by WorMzy on 2011-04-02
Do you get a context menu anywhere else? Like, if you right-click your desktop, do you get a context menu with "Create Folder, Create Launcher, etc"?

Edit:

After checking something, I think your panel is in lockdown mode.

Open gconf-editor (Alt+F2; gconf-editor; run) and browse to /apps/panel/global/, check the locked_down key, and make sure that the checkbox is unchecked. Then restart the panel (Alt+F2; pkill gnome-panel; run).

---

### Post by Dexdrex007 on 2011-04-02
> **WorMzy said:**
> Do you get a context menu anywhere else? Like, if you right-click your desktop, do you get a context menu with "Create Folder, Create Launcher, etc"?

Edit:

After checking something, I think your panel is in lockdown mode.

Open gconf-editor (Alt+F2; gconf-editor; run) and browse to /apps/panel/global/, check the locked_down key, and make sure that the checkbox is unchecked. Then restart the panel (Alt+F2; pkill gnome-panel; run).

MANY THANKS TO YOU BRO! 

its ok now. any idea how i got it to lock down mode? so i won't do that again? Thanks again!

---

### Post by WorMzy on 2011-04-02
No idea. I guess you either did it by accident, or someone else did it. I don't think you can activate it accidentally.

---

### Post by Dexdrex007 on 2011-04-02
> **WorMzy said:**
> No idea. I guess you either did it by accident, or someone else did it. I don't think you can activate it accidentally.

no, im the only one using my laptop. 

guess i did it by accident.

---

