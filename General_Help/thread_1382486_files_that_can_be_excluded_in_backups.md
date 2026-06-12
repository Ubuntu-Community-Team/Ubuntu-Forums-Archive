---
title: "files that can be excluded in backups"
date: 2010-01-16
forum: General Help
---

### Post by bluelightav on 2010-01-16
Hi everybody,
working on backups in general I noticed that the backups get quite large in size and I am wondering which files can be safely omitted. 


./*.gvfs
./*Trash*
*.thumbnails
*urlclassifier3.sqlite
*/*xapiandb (for Recoll users)
*/.wine
*/.local

Pls add here if you know of more files/folders. The backup should contain all files needed for a full restore.

---

### Post by warfacegod on 2010-01-16
This is what you want:

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by john newbuntu on 2010-01-16
I would also exclude 
.thumbnails,
.mozilla/firefox/*.default/Cache/*
leave only the last file in .compiz/session
.adobe/Flash_Player/

---

### Post by warfacegod on 2010-01-16
This is for removing things from ubuntu. Make your OS smaller, ergo make your backup smaller.

[http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager]("http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager")

---

