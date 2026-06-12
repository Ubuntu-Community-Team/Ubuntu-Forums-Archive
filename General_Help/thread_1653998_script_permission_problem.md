---
title: "script permission problem"
date: 2010-12-27
forum: General Help
---

### Post by ishokenmei on 2010-12-27
Hi, everyone.  I wrote a script with permission "-rwx--x--x" and it run fine.  I tried to disable "read" by changing it to "--wx--x--x" but it said "Permission denied".  I wonder if I could make it write and execute only without using "sudo".  Thanks in advance.

---

### Post by sisco311 on 2010-12-27
You can't. A script is just a plain text file with a list of commands. The interpreter needs read access to it.

---

