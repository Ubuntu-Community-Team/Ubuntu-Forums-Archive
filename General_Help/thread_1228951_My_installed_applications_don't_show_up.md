---
title: "My installed applications don't show up"
date: 2009-08-01
forum: General Help
---

### Post by Natpjohnson on 2009-08-01
Hello, I've recently tried to install various well known programs however they do not show up anywhere.  Even in the home folder they do not show up.  It's like they were never installed, but I know for a fact I watched them being installed in the terminal and everything.  The application I am most concerned with is ies4linux(mainly because its in the way of my WoW playing).  I did the whole cabextract (already have wine) and downloaded the ies4linux file.  It runs the installer for it, however it doesn't show in the applications or home folder.  Any help is greatly appreciated, Thank you.

---

### Post by TeoBigusGeekus on 2009-08-01
Type 
```
whereis ies4linux
```
It will show where the binaries are installed.
Right click the menus->Edit menus
go to Games(or wherever you like) and select new item. Give it a name and give /path/to/binary/ies4linux for command.
Of course all the above apply only if you can run the app typing /path/to/binary/ies4linux in terminal.

---

### Post by michy99 on 2009-08-01
Wine programs install in a hidden folder named .wine in your home folder. To see hidden folders in the file manager, press Ctrl+h.

---

