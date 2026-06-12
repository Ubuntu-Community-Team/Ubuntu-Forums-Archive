---
title: "logging onto kde as root"
date: 2006-05-10
forum: General Help
---

### Post by mcioffi on 2006-05-10
Hi,  New interface for me.  dosc say go to system->administration->login security tab, but there is no ->administration tab, never mind security tab

Any advice would be nice, I need to deit a pile of conf files, and I want to try out the desktop.

Thanks, M

---

### Post by aysiu on 2006-05-10
Two things:

1. The docs you're reading are for Gnome

2. Why do you want to log in as root?
If you want to temporarily browse as root, press Alt-F2 and type ```
kdesu konqueror
```

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by mcioffi on 2006-05-10
I was hoping to use the desktop editor (kate) to edit conf files for apache and other stuff I am hoping to get working.  New OS for me and I wanted to use something other than vi, since my navigations skills are poor (old windows user) and I thought kate would make life simpler while I get started and learn the file layout. 

M.

---

### Post by aysiu on 2006-05-10
[QUOTE=mcioffi]I was hoping to use the desktop editor (kate) to edit conf files for apache and other stuff I am hoping to get working.  New OS for me and I wanted to use something other than vi, since my navigations skills are poor (old windows user) and I thought kate would make life simpler while I get started and learn the file layout.[/QUOTE] Alt-F2 ```
kdesu konqueror
``` is perfect for this. You'll still be logged in as user, but you get a temporary Konqueror window that can browse as root and edit files with Kate as root. Once you close that Konqueror window, you're still user.

It's a lot easier than logging out of user, logging as root, making changes, logging out of root, and logging back in again as user.

---

### Post by mcioffi on 2006-05-10
Thanks to all!!!   Tried it, works PERFECTLY   Thanks again!!!

M.

---

