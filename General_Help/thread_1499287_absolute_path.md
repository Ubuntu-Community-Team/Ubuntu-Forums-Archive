---
title: "absolute path"
date: 2010-06-01
forum: General Help
---

### Post by mqlmql on 2010-06-01
How do I express absolute path regardless of your current working directory?

ex) /home/username/aaa.exe

---

### Post by ba_saish on 2010-06-03
If you are asking how to get the absolute path to current working directory then use the command "pwd"

---

### Post by BoneKracker on 2010-06-03
> **mqlmql said:**
> How do I express absolute path regardless of your current working directory?

ex) /home/username/aaa.exe

You've got it right.

It should start with a /, which causes the shell to interpret the path as starting at the top of the root filesystem (an "absolute path").
If you start it without a leading /, then the shell interprets the path as starting at $PWD (a "relative path").

---

### Post by mqlmql on 2010-06-05
thanks

---

