---
title: "cp -dpr  --  As root?"
date: 2009-07-04
forum: General Help
---

### Post by Muscovy on 2009-07-04
I'm trying to write a C++ program to copy a file into a directory that the user doesn't own, /home/help . The command cp -dpr works in terminal, if I log in as root, but writing
```

system("sudo su");
system("cp -dpr ~/help /home");

```
Doesn't work. Any ideas?

---

