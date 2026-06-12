---
title: "installing a .deb package"
date: 2009-08-24
forum: General Help
---

### Post by diggedy on 2009-08-24
Im only able to install these from terminal. When using gnome I used to double click on them to install but now im using KDE it seems that archive manager is the default program to open it with. Does anyone know which program I need to select to open these files with to install them when double clicking on them?

---

### Post by philcamlin on 2009-08-24
[LIST]
[*]                                        To install a .deb file, simply Right click on the .deb file, and choose                          Kubuntu Package Menu->Install Package.
[*]               Alternatively, you can also install a .deb file by opening a terminal and typing:[INDENT]sudo dpkg -i package_file.deb[/INDENT]
[*][INDENT]To uninstall a .deb file, remove it using **Adept**, or type:[/INDENT]
[*][INDENT]sudo apt-get remove package_name[/INDENT]
[/LIST]

---

