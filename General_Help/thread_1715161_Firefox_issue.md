---
title: "Firefox issue"
date: 2011-03-26
forum: General Help
---

### Post by nmyrick on 2011-03-26
Actually, I should probably post this on Mozilla's forums, but I was wondering if anyone could help me out.

The issue I am having is that I can't set FF to use OpenOffice as the default to open downloaded word documents.  When I try to choose an application as the default in FF preferences, it directs me to whatever folder I last opened in nautilus, rather than Ubuntu's application selection menu.

It also does not give me the option to run a command.  So, my question is, what file do I need to direct FF to in order to make it use OpenOffice by default?

---

### Post by Tamlynmac on 2011-03-26
> nmyrick
When I try to choose an application as the default in FF preferences, it  directs me to whatever folder I last opened in nautilus, rather than  Ubuntu's application selection menu.

When FF preferences opens the file manager (asking you which app to use), on the left side of the window is your home directory and another one called "file system". Select "file system" and then find the "usr" folder on the right side of the window. Double click on "usr/bin/oowriter". Most all your app executables are located in that folder.

This will set the file to open in OO writer. I've often wondered why it wasn't set to default the menu with an option to open an executable that isn't listed in the menu.

Good Luck & hope this helps.

---

