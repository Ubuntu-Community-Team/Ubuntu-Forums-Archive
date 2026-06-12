---
title: "Run Script as User.. not working?"
date: 2010-11-20
forum: General Help
---

### Post by zzzBrett on 2010-11-20
I am trying to set up dropbox to run on startup on my server running ubuntu 10.04. When I add it (via webmin) to the startup tasks, it creates it in /etc/init.d/Dropbox, and starts fine, but runs as root. I want it to run as user "brett".

I have tried doing a chmod +s dropboxd and setting the owner to "brett", but it still runs as root. I have also tried running sudo -u brett dropboxd but for some reason the program has errors and doesn't run if I do that.

Any suggestions?

---

### Post by luigi_mb on 2010-11-20
> **zzzBrett said:**
> I am trying to set up dropbox to run on startup on my server running ubuntu 10.04. When I add it (via webmin) to the startup tasks, it creates it in /etc/init.d/Dropbox, and starts fine, but runs as root. I want it to run as user "brett".

I have tried doing a chmod +s dropboxd and setting the owner to "brett", but it still runs as root. I have also tried running sudo -u brett dropboxd but for some reason the program has errors and doesn't run if I do that.

Any suggestions?

You may want to use chown to change ownership.

```

man chown

```

/luigi

---

### Post by Hippytaff on 2010-11-20
+1 luigi's suggestion
And maybe have a look at this link  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by I8NY on 2010-11-20
in the script do
```
su username -C command
```this will launch as whatever user it is set to be.

---

