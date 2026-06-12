---
title: "Problem with ownning files after reinstall"
date: 2010-11-24
forum: General Help
---

### Post by mahmoodn on 2010-11-24
I have reinstalled Ubuntu without formatting /home. After login, I have not permission to some of my files. For example I want to extract a tar.gz file:
```
mahmood@localhost:sources$ tar jxf lm_sensors-3.2.0.tar.bz2
tar: lm_sensors-3.2.0: Cannot mkdir: Permission denied
tar: lm_sensors-3.2.0/README: Cannot open: No such file or directory
tar: lm_sensors-3.2.0/INSTALL: Cannot open: No such file or directory
tar: lm_sensors-3.2.0/COPYING: Cannot open: No such file or directory
....

```

this is the detail of that file:
```
mahmood@localhost:sources$ ls -l lm_sensors-3.2.0.tar.bz2
-rw-r--r-- 1 [COLOR="Red"]1001 1001[/COLOR] 165008 2010-10-10 22:54 lm_sensors-3.2.0.tar.bz2

```
Please notice the user and group fields. Why they are shown as numbers?

---

### Post by WorMzy on 2010-11-24
Because you, presumably, created a *second* user on your previous installation of Ubuntu, and used that's /home/username folder as the home folder for the *first* user on this install. UIDs start at 1000 and continue upwards.

Simply run
```
sudo chown -R $UID:$UID ~
```

and it should change the ownership of the files to your user.

EIDT: You might got a permission denied error for the .gvfs folder, but that's normal and can be safely ignored.

---

### Post by mahmoodn on 2010-11-24
Really thanks for that :) however I didn't get that error :D because there was no files there. Thanks again

---

