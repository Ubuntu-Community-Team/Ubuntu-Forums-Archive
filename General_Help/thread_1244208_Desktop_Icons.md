---
title: "Desktop Icons"
date: 2009-08-19
forum: General Help
---

### Post by jvc26 on 2009-08-19
Hi there, just a brief question, my desktop no longer shows the icons of currently mounted drives/files and folders in the desktop folder. I can't remember for the life of me how to make this work again - any help would be much appreciated.

Cheers,

Il

---

### Post by lian1238 on 2009-08-19
> **Illuvator said:**
> Hi there, just a brief question, my desktop no longer shows the icons of currently mounted drives/files and folders in the desktop folder. I can't remember for the life of me how to make this work again - any help would be much appreciated.

Cheers,

Il

Did you disable it in /apps/nautilus/preferences/show_desktop ?
If so, just run (Alt+F2) **gconf-editor**
and navigate to  /apps/nautilus/preferences/ and check show_desktop.

---

### Post by jvc26 on 2009-08-19
Cheers for that - solved it - I hadn't disabled it - in UNR it is off by default, so moving back to the original setup demanded re-enabling and I wasnt sure where that was.

Cheers,

Il

---

