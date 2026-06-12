---
title: "Is it possible to clean up the right click menu when selecting folders?"
date: 2010-02-05
forum: General Help
---

### Post by Rytron on 2010-02-05
Hi.
Is it possible to clean up the right click menu when selecting folders? I know you can clean up for a file by right clicking / properties / open with and then removing the items. This method is not possible for folders.

Note: I ususally right click a folder when it contains video files. I try out various video players and before long there are loads of items when I right click a folder and choose Open with.

---

### Post by Rytron on 2010-02-09
Anyone?

---

### Post by mc4man on 2010-02-09
```
gedit ~/.local/share/applications/mimeapps.list
```

look for this line and remove entries as desired - at a min. just leave like this
> inode/directory=nautilus-folder-handler.desktop;

(note how there are no spaces between entries on any particular line and entries always end with ;

---

### Post by Rytron on 2010-02-10
Gracias mc4man. :p

---

