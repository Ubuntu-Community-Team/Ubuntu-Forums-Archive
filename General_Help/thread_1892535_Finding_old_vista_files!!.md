---
title: "Finding old vista files!!"
date: 2011-12-08
forum: General Help
---

### Post by Andyjp1 on 2011-12-08
Hi guys, my partner has a Dell laptop with Vista installed, unfortunately vista isn't loading anymore and the system requires a factory reset.
Due to not backing up her data for a number of week she wishes to try and recover it all before I have to reset it, I have downloaded ubuntu, recommended by a friend but am not sure how to find her old files to back them up.
Can anyone help?

Thanks in advance.

---

### Post by Mark Phelps on 2011-12-08
Personal files in Vista are no longer located in MyDocuments; instead, they are located C:\Users\<username>\AppData\Local\ ... and ...\AppData\Roaming\...

AppData is a hidden folder, so it's not seen by default.

As to other files -- like IE favorites, FF bookmarks, data files -- they are all over the place.

Something you should consider is imaging off the Vista setup to an external drive in such a way that the image can be "mounted" for later browsing.  You will need a Windows PC to do this, as the Window imaging products will only run there.

Couple of Windows products to explore: Macrium Reflect and EASEUS ToDo Backup.

Both of these allow you to create a Boot CD, but since the CD is designed for Restores, I don't know if you can make backups with it. If you can, you could hook up an external drive to her PC, backup Vista to that drive, and later, hook up the same drive to another PC, mount the backup and copy files from it.

---

