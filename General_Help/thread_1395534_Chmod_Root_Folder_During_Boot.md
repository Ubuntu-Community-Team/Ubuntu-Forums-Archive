---
title: "Chmod Root Folder During Boot"
date: 2010-02-01
forum: General Help
---

### Post by Cefari on 2010-02-01
Recently my sys folder got wiped somehow and I'm trying to replace the files within. However when booting up from a live cd I can't access the sys nor the root folder. Is there anyway I can change the permissions on the root folder during bootup so that anyone cane mess with it?

---

### Post by garvinrick4 on 2010-02-01
> **Cefari said:**
> Recently my sys folder got wiped somehow and I'm trying to replace the files within. However when booting up from a live cd I can't access the sys nor the root folder. Is there anyway I can change the permissions on the root folder during bootup so that anyone cane mess with it?
Do you boot the live cd and in places drop down menu is the drive on the menu?

Click on partition and mount it on desktop.

Alt/F2    

Type gksudo nautilus

Will say root on top of list.

Find partition on list you want to have root access and open it.
You will have root permissions.

---

