---
title: "wine problem"
date: 2010-08-22
forum: General Help
---

### Post by tal32123 on 2010-08-22
i had wine, but when i uninstalled it it left a bunch of the folders from stuff i previously installed. how do i remove those? (i want to do it the correct way and not leave any junk in the registry and whatnot.........idk if that makes sense im kind of a noob here)

---

### Post by WorMzy on 2010-08-22
Just open your home folder, press Ctrl+H to show the hidden files, and delete the .wine folder.

Ubuntu doesn't have a registry. Well, it *does*, gconf, but that's not the same as the Windows registry. Deleting .wine won't mess anything up, and wine doesn't use gconf, so you don't need to worry about redundant entries. (You don't need to worry about redundant entries, period.)

---

### Post by tal32123 on 2010-08-22
> **WorMzy said:**
> Just open your home folder, press Ctrl+H to show the hidden files, and delete the .wine folder.

Ubuntu doesn't have a registry. Well, it *does*, gconf, but that's not the same as the Windows registry. Deleting .wine won't mess anything up, and wine doesn't use gconf, so you don't need to worry about redundant entries. (You don't need to worry about redundant entries, period.)

thanks, i still however have the shortcuts in my menu though, any idea how i can delete those?

---

### Post by Vaphell on 2010-08-22
maybe rightclick on menus, edit menu and delete stuff from wine subtree?

---

### Post by tal32123 on 2010-08-22
> **Vaphell said:**
> maybe rightclick on menus, edit menu and delete stuff from wine subtree?

would that actually get rid of everything? and if i reinstall wine, would that put the wine directory back (if i reinstall i want the directory back, but not with everything ive previously installed.)?

---

