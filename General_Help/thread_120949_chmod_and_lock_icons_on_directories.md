---
title: "chmod and lock icons on directories"
date: 2006-01-23
forum: General Help
---

### Post by ice60 on 2006-01-23
hi, i want to change the permissions of a directory i made but when i do chmod 755 name_of_folder only the permission of the directory i can see is changed, the directory has a lock icon too which i think is causing the problem :( when i go into the directory nothing is executable, everything is - 644. how can i make the contents/sub-directories of the directory 755 too?

here's a picture.

---

### Post by professor_chaos on 2006-01-23
chmod -R 744
this "-R" will change everything in that folder and below to those permissions.

---

### Post by ice60 on 2006-01-24
[QUOTE=professor_chaos]chmod -R 744
this "-R" will change everything in that folder and below to those permissions.[/QUOTE]
thanks, professor_chaos. it looks like it worked, but the contents was corrupt so now it says it can't determine the permissions :rolleyes: i'm trying to convert cursors made for XP to Ubuntu cursors.

i think i've used -r in the past for folders, does it matter if it's a r or R?

---

