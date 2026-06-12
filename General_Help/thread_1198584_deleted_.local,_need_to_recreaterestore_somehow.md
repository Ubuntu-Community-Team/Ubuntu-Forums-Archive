---
title: "deleted .local, need to recreate/restore somehow"
date: 2009-06-27
forum: General Help
---

### Post by austin987 on 2009-06-27
When removing some cruft in ~/.local, I accidentally rm -rf'ed the entire folder...while it's not fatal, all apps still work, installing anything with wine gives tons of errors/warnings:
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/austin/.local/share/applications/wine-extension-aa.desktop"
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/austin/.local/share/applications/wine-extension-chm.desktop"
No directories in update-desktop-database search path could be processed and updated.

Obviously, a reinstall would be overkill. Surely there's some command to create a default .local, with the proper files/information...

---

### Post by dcstar on 2009-06-27
> **austin987 said:**
> When removing some cruft in ~/.local, I accidentally rm -rf'ed the entire folder...while it's not fatal, all apps still work, installing anything with wine gives tons of errors/warnings:
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/austin/.local/share/applications/wine-extension-aa.desktop"
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/austin/.local/share/applications/wine-extension-chm.desktop"
No directories in update-desktop-database search path could be processed and updated.

Obviously, a reinstall would be overkill. Surely there's some command to create a default .local, with the proper files/information...

Just create a new user account, log into it then log out, and then copy the folder (set permissions to the existing account).

---

