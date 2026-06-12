---
title: "Logging on as root?"
date: 2006-06-04
forum: General Help
---

### Post by gotvols on 2006-06-04
Can you log on as root in Ubuntu 6.06?  I was trying to copy a file into the usr/bin folder and it told me I didn't have the permissions.  I logged off and tryed to log on as root and it won't let me.

---

### Post by Meads on 2006-06-04
From terminal do this "sudo cp file dirname/filename" without the quotes ofcourse :)

---

### Post by xXx 0wn3d xXx on 2006-06-04
[QUOTE=gotvols]Can you log on as root in Ubuntu 6.06?  I was trying to copy a file into the usr/bin folder and it told me I didn't have the permissions.  I logged off and tryed to log on as root and it won't let me.[/QUOTE]
Don't run as root all the time and try to not use it at all. Use sudo. To move the file try this:

> sudo cp name/of/file /directory/where /you want it/

---

### Post by tonyr on 2006-06-04
Read this:
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by gotvols on 2006-06-04
Thanks. I got it to work.

---

