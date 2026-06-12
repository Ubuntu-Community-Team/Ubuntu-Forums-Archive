---
title: "Installed some fonts... core fonts gone"
date: 2010-04-15
forum: General Help
---

### Post by redgsturbo on 2010-04-15
Times New Roman is no longer showing up.... which sucks as everything is in it.  I tried reinstalling core fonts, and still doesn't show up... effects almost all my desktop applications.  Any idea how to fix or what info is required of me?

---

### Post by ajgreeny on 2010-04-15
> **redgsturbo said:**
> Times New Roman is no longer showing up.... which sucks as everything is in it.  I tried reinstalling core fonts, and still doesn't show up... [COLOR=Red]effects almost all my desktop applications.[/COLOR]  Any idea how to fix or what info is required of me?
Are there any apps in which it does work?  If so then you can be sure it, or they, are definitely installed.  Try searching for them ```
with locate Times_New_Roman
```then in terminal, navigate to the folder where they are and run ```
sudo fc-cache -f -v
``` That may update the font cache and make everything available to all apps.

---

### Post by redgsturbo on 2010-04-20
> **ajgreeny said:**
> Are there any apps in which it does work?  If so then you can be sure it, or they, are definitely installed.  Try searching for them ```
with locate Times_New_Roman
```then in terminal, navigate to the folder where they are and run ```
sudo fc-cache -f -v
``` That may update the font cache and make everything available to all apps.

that doesn't find anything :confused:

---

