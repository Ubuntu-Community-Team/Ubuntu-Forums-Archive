---
title: "Replacing icons?"
date: 2010-07-10
forum: General Help
---

### Post by Cam! on 2010-07-10
I would like to replace the app icons for Google Chrome and Rhythmbox. Where do I store the replacement icons? Every time I do this, Google + RB end up having the default, ambiguous app icon (The gear).

---

### Post by drs305 on 2010-07-10
Where are you seeing the icons?

In most areas (such as the panel), you can right click the icon, select Properties, then click on the icon to select a new icon/location.

For items under the Main Menu, right click the Main Menu icon, "Edit Menu", then right click on the app you want to change to access its Properties.

---

### Post by lidex on 2010-07-10
If that doesn't work, try putting the icon into this directory:
```
/usr/share/app-install/icons/
``` 
and maybe:
```
/usr/share/pixmaps/
```
It may help to open gedit as root:
```
gksudo gedit
```
Use nautilus to browse to
```
 /usr/share/applications/
```
and drag the desktop configuration file of the launcher in question into gedit. (Don't double-click in nautilus or 'right-click>open' as it will run the app.) The line starting with 'Icon=' gives the name of the icon file. You can change the filename there to a different one or find the icon needed and then overwrite that icon with the one desired in the app-install directory.

---

