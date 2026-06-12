---
title: "home folder"
date: 2010-01-26
forum: General Help
---

### Post by kevinorourke2008 on 2010-01-26
Hello everybody,
I  am just about to upgrade to 9.10 using update manager and I thought it best to make a copy of my home folder. Is there an easy way to make a copy to a usb hard drive or do I have to copy each item in the home folder individually?

Cheers kev:D

---

### Post by r_s on 2010-01-26
just create an archive of the home folder and save it

---

### Post by Vaphell on 2010-01-26
home folder is no different than any other folder, just go 1 level up ( to /home ), select your home dir and copy it. After copying make sure nothing was left out (properties, size, number of files and directories should be the same)

---

### Post by SuperSonic4 on 2010-01-26
From your home directory (/home/user) and one line at a time

```
cd ..
cp -av *user* /media/USB
```

user is your username

v is verbose so it tells you what's going on.
a is archive and implies R (recursive), d (do not preserve symlinks) and --preserve (keeps file ownership etc)

---

