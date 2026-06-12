---
title: "Help with locked files"
date: 2009-09-25
forum: General Help
---

### Post by onespeedbiker on 2009-09-25
This is not a major issue. Every time I restore a file from Trash, they are restored locked. Ubuntu will let me change the permissions back, but it seems a waste of time. Also, I saved some jpeg files on a dvd and when I pasted them back, they were all locked as the restore files. Again it doesn't take much to change the permissions back, but is there anyway to re-configure Ubuntu to allow me to transfer or restore files, without changing the permissions?

---

### Post by credobyte on 2009-09-25
Not sure about how would you fix it, tough, it shouldn't be so ( bug ? ).

---

### Post by CatKiller on 2009-09-25
I have no idea what's going on with your Trash, but the DVD behaviour is normal. DVDs are necessarily read-only, and the files that you copy from a DVD inherit that attribute.

---

### Post by pcjunkie on 2009-09-25
Correct.
Any ISO image or DVD once trashed will restore as read only.
You need to chown or chmod to manipulate them.

---

