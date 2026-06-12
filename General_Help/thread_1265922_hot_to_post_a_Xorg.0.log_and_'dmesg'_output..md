---
title: "hot to post a Xorg.0.log and 'dmesg' output."
date: 2009-09-14
forum: General Help
---

### Post by kpholmes on 2009-09-14
im working on a bug in launchpad and a dev is requesting for me to post a fresh Xorg.0.log and 'dmesg' output.

how do i do that?

---

### Post by jocko on 2009-09-14
> **kpholmes said:**
> im working on a bug in launchpad and a dev is requesting for me to post a fresh Xorg.0.log and 'dmesg' output.

how do i do that?
Well. Xorg.0.log is a file in /var/log, so just attach that file to the bug report.
To get the dmesg output in a file, type this command in a terminal:
```
dmesg > ~/dmesg.txt
```
That will give you the dmesg output in the file dmesg.text in your home directory.

---

### Post by kpholmes on 2009-09-14
sweet! thanks.

---

