---
title: "Messed with /etc permissions"
date: 2006-04-04
forum: General Help
---

### Post by BrownieMan on 2006-04-04
Now that I messed with the permissions in /etc (I changed all the permissions to one user) what can I do to fix it? I can't use Synaptic now.

---

### Post by htinn on 2006-04-04
I assume you want this:

[https://wiki.ubuntu.com/LostPassword](https://wiki.ubuntu.com/LostPassword)

Then, again... Maybe I have no idea... :(

---

### Post by BrownieMan on 2006-04-04
Well I need some way of resetting all the files and folders to their correct permissions.

---

### Post by htinn on 2006-04-05
Okay, I think I understand. You probably chmod'd everything in /etc to something like 400 or 600? Maybe you should try and chmod the files to 644. You might have to change a few things to 664 (like printcap, maybe), but this should get things going again (assuming you didn't change the permissions recursively).

---

### Post by Sutekh on 2006-04-05
Err you probably want /etc to have 755 permissions, not 644.
```
sudo chmod -R 755 /etc
```The -R makes it filter through subfolders.

644 will not allow execution of files in /etc.

---

