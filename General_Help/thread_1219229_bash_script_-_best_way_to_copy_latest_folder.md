---
title: "bash script - best way to copy latest folder"
date: 2009-07-21
forum: General Help
---

### Post by Hawk__0 on 2009-07-21
I was wondering how I would be able to make a script determine which is the latest folder, so it can copy it to another location.  IE: lets say every day a folder is created.  Is there a way to make bash know which was last modified so I can include it in some sort of copy command?

---

### Post by prem1er on 2009-07-21
Do you mean every time a folder is created in some directory you want to be able to store that folder in a variable and copy it somewhere?  So, you want to actually 'watch' a directory for changes?

---

### Post by Hawk__0 on 2009-07-21
Yes, but no.  I dont want to watch it.  It's for a script that will copy backup folders that are created daily.

When I plug in an external hard drive, I expect to run this script to copy all the data, mount/unmount, etc all automatically.  I'm just stuck on how to determine which folder is the newest..

---

### Post by prem1er on 2009-07-21
```
ls -lrt
```

Gives you the creation date/time of a folder.  You can grep that information out and find the latest one.  Or you could use,

```
ls -t
```

which will arrange the folders in order of when they were modified.

---

### Post by Hawk__0 on 2009-07-21
Thanks for the suggestions.  I have stuck with a simple listing of the files in the backup directory, and making the user manually type in which folder to back up (it's 2 digits, no biggy).

---

