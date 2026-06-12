---
title: "Firefox 3.6.13 (upgrade from 9.04 to 9.10)"
date: 2011-01-15
forum: General Help
---

### Post by Brad55 on 2011-01-15
I had this problem today not being able to import my bookmarks. I tried uninstalling Firefox and reinstalling and that did not work. But for some reason it would not pull my bookmarks in. I even tried to pull in a backup .json file from Firefox but it just would not do it.

Has any body else had this problem?

I did find a way of getting my bookmarks in to Firefox. 
1. Open up gedit and then open your bookmarks.html file. (could be one from another computer that you backed up)
2. Select all and copy.
3. Open up the bookmarks.html file under .mozilla in your home folder.
4  Select all and paste from other bookmarks.html file.
5. Then save.

All your bookmarks should be there.

I have never had this problem before and I have 4 different computers that I have done this to. I even checked the permissions on the file and set the permission so all could do any thing to the file.

---

### Post by lovinglinux on 2011-01-15
Is not recommended to use the bookmarks.html file, because that is no longer used by Firefox since version 2.0. Bookmarks are stored now in the places.sqlite database file. 

If you bookmarks are not working, then delete places.sqlite and restore a json backup.

---

