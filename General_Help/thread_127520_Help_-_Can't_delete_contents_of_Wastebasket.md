---
title: "Help - Can't delete contents of Wastebasket"
date: 2006-02-09
forum: General Help
---

### Post by MJSOnline on 2006-02-09
Hi all.

I have a problem with file permissions.

I have backed up a fair bit of programs from cover cd/dvds' into a folder on my harddrive. I have now burnt the files/folders to DVD and want to delete them from my harddrive, BUT Ubuntu wont let me.

How do I fix this? I have over 20 folders to delete. I have changed the permissions to Owner/Group/Others to ON/ticked, but it won't delete.

Is there a fast way to delete them all from the Wastebasket? Many thanks in advance. Matthew

---

### Post by Ocxic on 2006-02-09
is the owner of the files root, if they are then you won't be able to delete them unless you are root.

---

### Post by MJSOnline on 2006-02-09
No.  The file owner is me...  odd... M

---

### Post by kingsidy on 2006-02-09
this will forcefully empty the trashcan:
> sudo rm -fr $HOME/.Trash/

---

### Post by MJSOnline on 2006-02-09
Er..... nope.  that did not work... M

---

### Post by MJSOnline on 2006-02-09
Anyone?  Matthew

---

### Post by Greg2 on 2006-02-09
I believe kingsidy made a small typo? It’s```
sudo rm –rf $HOME/.Trash/*
```

---

