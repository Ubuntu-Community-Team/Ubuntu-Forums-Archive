---
title: "Copying from windows partition to WINE"
date: 2010-09-10
forum: General Help
---

### Post by deviator on 2010-09-10
i have windows partition i'm unable to access through dual boot.

i'm wondering if i could copy a game over to wine (warcraft 3) as i don't have the discs available.

---

### Post by Mark Phelps on 2010-09-11
Basically -- NO.  It's not a problem with Wine per se; it's a generic problem with Windows apps.

In addition to Program Files entries and data files, they create LOTS of registry entries.  You would have to find and copy every single registry entry -- and edit it to point to the correct new location.

This is why nearly all the apps that supporting migrating to a new OS or machine only mention settings and files.  They don't know how to handle registry setting migrations.

---

