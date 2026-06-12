---
title: "Invalid main menu item (corrupt shortcut)"
date: 2010-07-01
forum: General Help
---

### Post by veggen on 2010-07-01
After upgrading Opera browser, by old shortcut for it became invalid. The new was added but the old one stayed and is invalid. I can not remove it through normal means as it doesn't appear in the menu editing window but it's there in the menu. 
Is there any way to manually remove items from the menu? Or to rebuild the entire menu?

---

### Post by panos_thes on 2010-07-01
i got this issue too, i tried to reinstall and i got lots of errors :(

---

### Post by veggen on 2010-07-03
Ok, I solved this one. First, try deleting /usr/share/applications/opera.desktop. If this doesn't help try removing Opera completely ('complete removal' in Synaptic + delete ~/.opera) and reinstalling. This made menu config 'see' the invalid shortcut and let me delete it.

---

### Post by panos_thes on 2010-07-04
deleting just opera.desktop works fine, thanks!!  :)

---

