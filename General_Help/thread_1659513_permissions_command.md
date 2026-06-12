---
title: "permissions command"
date: 2011-01-04
forum: General Help
---

### Post by lex1 on 2011-01-04
commands trying to use


chown -R admin /path/to/folder
chmod u+rwX /path/to/folder 



ubuntu@ubuntu:/media/mac/Users$ ls
admin Shared
ubuntu@ubuntu:/media/mac/Users$ cd
ubuntu@ubuntu:~$ sudo chown -R admin /media/mac/Users/admin
chown: invalid user: `admin'
ubuntu@ubuntu:~$ sudo chown -R admin /media/mac/Users/
chown: invalid user: `admin'
ubuntu@ubuntu:~$


seems maybe my command might be incorrect?

lex1:guitar:

---

### Post by karthick87 on 2011-01-04
Post the output of,
```
ls /home
```

---

