---
title: "nautilus-actions-config symbolic link mimetype"
date: 2010-02-06
forum: General Help
---

### Post by phoenox on 2010-02-06
I have been trying to create a right click menu item to open the folder containing the target of a symbolic link.  It is working now, except that the menu item is show in the right click menu for all files, not just symbolic links.

mimetype says the links have type inode/symlink.  If I enter that into nautilu-actions-config then the menu item does not show up for any files, not even symbolic links.  I believe that nautilus-actions-config must be checking the mimetype of the target, not the link.

Is there any way that I can make this work?

---

