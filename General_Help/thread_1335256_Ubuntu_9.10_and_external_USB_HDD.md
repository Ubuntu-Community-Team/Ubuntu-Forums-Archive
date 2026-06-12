---
title: "Ubuntu 9.10 and external USB HDD"
date: 2009-11-23
forum: General Help
---

### Post by elf_noire on 2009-11-23
Hello,
I was having a working system and it is gone after running update to 9.10.

I am just wondering,
What kind of a stupid system is this, which can not find a connected USB HDD?
Which also screewes everything after an update?

I am very mad because my external HD does not work any longer and I don't know why?

Elf

---

### Post by ptn107 on 2009-11-23
So when you plug it in nothing appears in /media/ or Places -> Computer?  Plug it in and post the output of:
```
uname -a && ls -l /media/
```

---

### Post by steven1664 on 2009-11-23
You could try sudo chmod 777 /media maybe there is a permissions issue.  Then when you are done just change the permissions back to what they were set at originally.

---

