---
title: "trouble with ls command"
date: 2011-06-18
forum: General Help
---

### Post by blompy on 2011-06-18
Why does the following command tell me that the scalpel.conf file doesn't exist ?  I know it is there; I can navigate there through the GUI.


testuser@ubuntu:~$ ls -l /ect/scalpel/scalpel.conf
ls: cannot access /ect/scalpel/scalpel.conf: No such file or directory
testuser@ubuntu:~$

---

### Post by hawthornso23 on 2011-06-18
could just be  spelling.

/ect/...       instead of         /etc/...

---

### Post by blompy on 2011-06-18
haha

thx, that helped


Linux is seems mystified until you realise the simple mistakes your making.

---

### Post by amauk on 2011-06-18
Use tab completion
avoids typos and saves generally reduces typing

Eg,
```
ls /e<tab>/sca<tab>
```

---

### Post by nzjethro on 2011-06-18
> **amauk said:**
> Use tab completion
avoids typos and saves generally reduces typing

Eg,
```
ls /e<tab>/sca<tab>
```

Wow, didn't know about that. Very useful. :D

---

