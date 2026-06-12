---
title: "contextual menu help for PlayonLinux"
date: 2011-10-06
forum: General Help
---

### Post by watgrad on 2011-10-06
I would like to fix my contextual menus to open Word Files from a PlayonLinux installation of Office.

I'm just not sure of how to get the desktop file for wine DOC files to open the file once PLAYONLINUX starts word...

This is the code that PLAYONLINUX created for doc files:
```
[Desktop Entry]
Type=Application
Name=Word
MimeType=application/msword;
Exec=env WINEPREFIX="/home/leej/.PlayOnLinux/wineprefix/Office2003" wine start /ProgIDOpen DOCfile %f
NoDisplay=true
StartupNotify=true
```

When you try to open a doc file with this contextual menu entry it throws an error message "There is no Windows program configures to open this type of file." (A Windows dialogue box)

Can anyone tell me how to create the nautilus contextual entries for PlayonLinux applications?
Thanks

---

### Post by watgrad on 2011-10-11
anyone?

---

