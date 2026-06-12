---
title: "Help changing file type"
date: 2011-01-16
forum: General Help
---

### Post by thebrian on 2011-01-16
A while ago, I installed a windows application (on wine) called Max/msp. I have uninstalled it, and removed wine from my system (deleting ~/.wine as well), but now I'm left with some files thinking they are "Max Externals." How do I fix this/restore to the default file types? Thanks

---

### Post by coldraven on 2011-01-16
Try right clicking on the file and select "Open with", "Other Application".
Scroll down until you find the one you want and make sure to check the box that says "Always use this application for this file type".

---

### Post by thebrian on 2011-01-17
I don't want to change what application opens the file by default. I want to change the file type. For example, in my file manager, any file with a .bin extension is called a "max external"

---

### Post by geirha on 2011-01-17
In ~/.local/share/applications, look in the files mimeinfo.cache and mimapps.list and remove the lines regarding that app. Do make backup copies first though, just in case.

---

### Post by thebrian on 2011-01-17
> **geirha said:**
> In ~/.local/share/applications, look in the files mimeinfo.cache and mimapps.list and remove the lines regarding that app. Do make backup copies first though, just in case.

There is no mimapps.list and in mimeinfo.cache there's only one line and doesn't have to do with that app.

---

### Post by geirha on 2011-01-17
Oops, typo. That's mimeapps.list.

---

