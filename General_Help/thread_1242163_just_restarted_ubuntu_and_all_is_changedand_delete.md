---
title: "just restarted ubuntu and all is changedand deleted?"
date: 2009-08-16
forum: General Help
---

### Post by tunznath on 2009-08-16
Hi
i just restarted my ubuntu 8.10 and all my folders on the desktop are gone, my documents folder is empty, my videos has some things in it, firefox has lost all its bookmarks, and all my preferences are changed, is there any way to get this back???

---

### Post by michy99 on 2009-08-16
Do you have /home on a separate partition? If so, it sounds like it isn't mounting.

Or did you perhaps log in as root?

---

### Post by tunznath on 2009-08-16
hi no home isnt on a seperate partition, and cold you please help with logging in as root, what are the terminal commands

---

### Post by michy99 on 2009-08-16
You don't need to log in as root. Open a terminal and enter these commands. Post the output here.```
pwd
ls -l /home
```

---

### Post by tunznath on 2009-08-17
Hi 
thanks  theres not that much output

ls -l /home
total 4
drwxr-xr-x 48 nath nath 4096 2009-08-17 08:52 nath

---

