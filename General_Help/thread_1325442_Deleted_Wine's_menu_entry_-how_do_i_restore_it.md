---
title: "Deleted Wine's menu entry -how do i restore it?"
date: 2009-11-13
forum: General Help
---

### Post by mmzdaniel on 2009-11-13
Title says it all, I accidently deleted wine's entry in the menu, an now I can't get it back. not even by re-installing. help me? ><"

---

### Post by nema.arpit on 2009-11-13
Try System>Preferences>Main Menu

---

### Post by mmzdaniel on 2009-11-13
Well thanks for the replay but no. i didnt just disable the entry, i accidently deleted it. its not even an option.

---

### Post by tubunu on 2009-11-13
Add a new menu entry, call it Wine and configure it. 

Wine
> Programs
Name: Programs
Icon: /usr/share/icons/Humanity/places/48/folder.svg

> Browse C:\ Drive
Type: Application
Name: Browse C:\ Drive
Command: xdg-open .wine/dosdevices/c:
Comment: Browse your virtual C:\ drive
Icon: /usr/share/icons/hicolor/48x48/places/folder-wine.png

> Configure Wine
Type: Application
Name: Configure Wine
Command: winecfg
Comment: Change application-specific and general Wine options
Icon: /usr/share/icons/hicolor/48x48/apps/wine-winecfg.png

> Uninstall Wine Software
Type: Application
Name: Uninstall Wine Software
Command: wine uninstaller
Comment: Uninstall Windows applications for Wine
Icon: /usr/share/icons/hicolor/48x48/apps/wine-uninstaller.png

---

### Post by mmzdaniel on 2009-11-13
Thanks guys, i noticed this small little "revert" button. im embarrased.

---

