---
title: "Failed to Open Directory Please Help"
date: 2012-07-26
forum: General Help
---

### Post by mamamia88 on 2012-07-26
A pic speaks a thousand words.  Here is the error message i'm getting when trying to open my micro sd card inserted in my computer.

---

### Post by ajgreeny on 2012-07-26
Open nautilus with root permissions using ```
gksu thunar
``` and see if that helps.  It looks as if you have some deleted files in trash on the card that can not be read or opened by your user.  Have you deleted files on the card just with the delete key?  That just moves them to a local trash-1000 on the card, though normally you would be asked if you want to delete the trash when you unmount any removable media.

You did unmount the card before removing it, I presume?

---

### Post by mamamia88 on 2012-07-26
> **ajgreeny said:**
> Open nautilus with root permissions using ```
gksu nautilus
``` and see if that helps.  It looks as if you have some deleted files in trash on the card that can not be read or opened by your user.  Have you deleted files on the card just with the delete key?  That just moves them to a local trash-1000 on the card, though normally you would be asked if you want to delete the trash when you unmount any removable media.

You did unmount the card before removing it, I presume?

i think i did don't remember.   tried running thunar as root same problem.    any other suggestions?  edit moving files to desktop with mv command telling me read only file system but they are still copying fine apperently.   just gonna format and see what happens

---

