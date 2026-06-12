---
title: "sudo nautilus trash/delete function puts trash where?"
date: 2009-09-28
forum: General Help
---

### Post by ToshibaLaptoplinux on 2009-09-28
When I sudo nautilus and delete a file or folder where does it go? It doesn't appear in either the root trash or the user trash. Is it automatically deleted or is it sitting someplace on the hard disk eating up space waiting for me to "empty the trash" somehow?

---

### Post by 3rdalbum on 2009-09-28
If you use the Delete function, then it is deleted and it no longer takes up space on your hard disk.

---

### Post by mc4man on 2009-09-28
On hardy the location is 
/root/.local/share/Trash/files
If navigating there in gksu nautilus then you'd need to go view -> show hidden files

While probably not recommended, gksu nautilus has it's own preferences menu. you could enable a delete command in edit -> preferences -> behavior 
 If so,  you best be sure first. (I wouldn't change any other setting's in roots prefs, and probably best to **leave the confirm option on.**

---

