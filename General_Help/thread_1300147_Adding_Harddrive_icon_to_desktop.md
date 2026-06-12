---
title: "Adding Harddrive icon to desktop"
date: 2009-10-24
forum: General Help
---

### Post by joelw135 on 2009-10-24
How do I add an icon for the main Harddrive to the desktop?

---

### Post by joelw135 on 2009-10-25
Someone must know how to do this!!!:KS

---

### Post by dv3500ea on 2009-10-25
Right click on desktop an click add launcher.
Choose type as file or folder.
Set path as '/'.
click on the icon to change the icon (you may have to search a lot in /usr/share/icons for the desired one).

---

### Post by joelw135 on 2009-10-25
> **dv3500ea said:**
> Right click on desktop an click add launcher.
Choose type as file or folder.
Set path as '/'.
click on the icon to change the icon (you may have to search a lot in /usr/share/icons for the desired one).

When I right click on the desktop and select "Create Launcher" there is only Location and Application in terminal. If I choose Location and '/'. as the path it gets an error not such path.

---

### Post by shadow120 on 2009-10-25
its just / no quotes or .

---

### Post by P4man on 2009-10-25
"main harddrive" is a concept that just doesnt work with linux. It makes no sense to have an icon that points to something that contains swap, running system processes and your home folder.

You can however add an icon for "my computer" or your home folder.
Press alt+F2 and run 
```
gconf-editor
```
browse to app>nautilus>desktop
enable computer_icon_visible and/or home_icon_visible

---

### Post by joelw135 on 2009-10-25
Thanks both worked, but I was unable to find a drive icon. Is such a icon available?

---

### Post by Vaphell on 2009-10-25
there are tons of icons in /usr/share/icons and /usr/share/pixmaps but for some reason they are unavailable from the launcher property window. Maybe copying some suitable icon to the directory recognized by the launcher would do the trick.

---

### Post by joelw135 on 2009-10-25
> **Vaphell said:**
> there are tons of icons in /usr/share/icons and /usr/share/pixmaps but for some reason they are unavailable from the launcher property window. Maybe copying some suitable icon to the directory recognized by the launcher would do the trick.
So far I haven't found a place that it can be seen. I will keep trying.

---

### Post by egalvan on 2009-10-25
Anything mounted under /media will automatically show an icon on the desktop.

Anything mounted under /mnt will NOT automatically show an icon on the desktop.


I use this to keep the internal drives off my desktop.


n.b.
removable media (such as floppy and CD/DVD ) will only show an icon once media is installed and recognized by the drive.

---

### Post by joelw135 on 2009-10-25
> **egalvan said:**
> Anything mounted under /media will automatically show an icon on the desktop.

Anything mounted under /mnt will NOT automatically show an icon on the desktop.


I use this to keep the internal drives off my desktop.


n.b.
removable media (such as floppy and CD/DVD ) will only show an icon once media is installed and recognized by the drive.

OK thanks good info to know. I am accustomed to OSX where all drives mounted are on the desktop.

---

