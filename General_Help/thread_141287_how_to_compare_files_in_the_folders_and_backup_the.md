---
title: "how to compare files in the folders and backup the latest one?"
date: 2006-03-08
forum: General Help
---

### Post by linuxcity on 2006-03-08
I backup my home folder from time to time. Now I have multiple copies of the home folders. I added some new files in different folders.

I want to combine all these folders into one without risking of loosing the update files in the folders.

What command/script or ultility that I can use to perform this task?

---

### Post by aysiu on 2006-03-08
I believe in Nautilus or Konqueror, you can just copy them over each other. When it tries to copy a file that already exists, it'll ask if you want to replace the current one with the new one. Just say "yes" or "no" as you see fit.

---

### Post by naked on 2006-03-08
rsync would be your best bet.

```
 rsync -av /stuff_to/backup /location/for_stuff
```

Not that rsync is particular in how you use your trailing '/'.  I'll show an example that is more helpful to illustrate:

```
 rsync -av /home/luke/documents /backup
```
This will "backup" the folder 'documents' to the folder 'backup'.  So it would result in /backup/documents/*

While:
```
 rsync -av /home/luke/documents/ /backup
```
Would "backup" everything IN 'documents' TO /backup.  So everything in your 'documents' folder would be copied into the 'backup' folder.  So /backup/*

Hope that makes sense.  If there is a trailing '/' on the source directory, it will copy the contents of the folder, not the folder itself.

Consult the rsync man page for more information
```
 man rsync 
``` 
:)

Luke

---

