---
title: "Backup files (~)"
date: 2010-02-13
forum: General Help
---

### Post by Monotoko on 2010-02-13
Hi Guys, Ubuntu appears to make backup files of any documents i create, this is fine when im on the desktop or whatever because they are hidden... but whilst im in filezilla, it shows them all, and makes it very hard to find the file i need. There have even been some cases of me trying to upload an entire folder to encrypt and give to my boss, and it still having the ~ files in.

Any idea how to stop this? I dont really need it and it is becoming an annoyance when i have folders with over 50 documents.

~Daniel

---

### Post by flippo on 2010-02-13
The ~ backups are not part of gnome directly, but part of your editor.  Vim makes ~ backups, but I set it to use a special directory.  Your most likely using gedit, which also makes ~ backups.  I believe there is an option in the preferences to disable backup files in gedit.

---

### Post by howefield on 2010-02-14
As already said, you can turn off this feature by going into the gedit (if that is what you are using) Edit > Preferences > Editor tab > Uncheck "Create a backup copy of files before saving".

Although I'd prefer simply to delete the backups whilst in Filezilla, they are easy to spot as you indicated, and then upload.

---

