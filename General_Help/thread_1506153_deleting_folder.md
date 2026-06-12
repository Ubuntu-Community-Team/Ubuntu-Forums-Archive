---
title: "deleting folder"
date: 2010-06-10
forum: General Help
---

### Post by sububtu on 2010-06-10
how do i delete a folder and its contents from terminal? when i tried to delete the folder it returns a- permission error,,-

---

### Post by Smart Viking on 2010-06-10
sudo rm -r /path/to/folder


Where "sudo" gives you root permission, "rm" says to remove something, and "-r" tells that it is a folder you want to delete.

But be careful with what you are deleting, suddenly you can do a big mistake! :)

---

### Post by sububtu on 2010-06-10
thanks,,,
rm -r  !!!!!!!! its working,,,,,:guitar:

---

