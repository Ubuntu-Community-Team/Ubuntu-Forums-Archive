---
title: "File permissions in the live session CD"
date: 2010-05-09
forum: General Help
---

### Post by diddybones on 2010-05-09
I  have broken my MBR and can now only enter 9.10 with the ubuntu start up  cd.

when i boot through he ubuntu live cd

I can see my mounted drive with all my files however i do not have the permissions to open or copy some of my files( music, films, pics) . id like to do this so i can transfer all my files to an external HDD and reformat start all over again

error when trying to open files


**You do not have the permissions necessary to view the contents of .....**

How can i get around this issue

---

### Post by bumanie on 2010-05-09
In terminal either > sudo -i or > gksudo nautilus - the first gives root access for the entire live session or until terminal is closed. the second should work the same as on an installation where one is given root access in graphical mode and you can navigate to your stuff via Places --> Computer --> Filesystem. Should stop file permission hassles.

---

### Post by diddybones on 2010-05-09
thanks a lot

gksudo nautilus

worked fine

---

### Post by bumanie on 2010-05-09
You should mark the thread as solved, then others with the same problem can follow the directions too.

---

