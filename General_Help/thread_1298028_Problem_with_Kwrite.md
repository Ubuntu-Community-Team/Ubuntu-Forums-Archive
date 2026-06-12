---
title: "Problem with Kwrite"
date: 2009-10-22
forum: General Help
---

### Post by sleepitoff on 2009-10-22
Whenever I open up a text file, I get this message: 

Configuration file "/home/jacob/.kde/share/config/kwriterc" not writable.
Please contact your system administrator.

How do I fix?

---

### Post by anubhavrocks on 2009-10-22
Check the permissions for the file:
ls -la /home/jacob/.kde/share/config/kwriterc

Also i hope your filesystem is not mounted read only.

---

