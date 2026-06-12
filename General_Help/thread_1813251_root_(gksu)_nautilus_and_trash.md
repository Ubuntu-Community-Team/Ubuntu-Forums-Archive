---
title: "root (gksu) nautilus and trash"
date: 2011-07-27
forum: General Help
---

### Post by spezticle on 2011-07-27
so i'm wondering what happens to files that i "send to trash" while using a root nautilus?
do they actually go to a 'trash' and if so how do i empty it?

---

### Post by yetiman64 on 2011-07-27
> **spezticle said:**
> so i'm wondering what happens to files that i "send to trash" while using a root nautilus?
do they actually go to a 'trash' and if so how do i empty it?

They are stored at /root/.local/share/Trash. There are two subfolders "files" and "info" at that location. The command ```
sudo rm -r /root/.local/share/Trash/
```from a terminal will remove the entire trash folder and the contents, next time a file is deleted as root the trash folder will be regenerated.

---

### Post by pqwoerituytrueiwoq on 2011-07-27
use [shift]+[del] to skip trash
root trash:
/root/.local/share/Trash/

---

### Post by spezticle on 2011-07-27
thanks ! :)

---

### Post by philinux on 2011-07-27
> **spezticle said:**
> so i'm wondering what happens to files that i "send to trash" while using a root nautilus?
do they actually go to a 'trash' and if so how do i empty it?

If you're using gksu nautilus then press ctrl h to show hidden files or View>show hidden. Navigate to the .Trash folder as mentioned in previous posts and delete it there.

---

