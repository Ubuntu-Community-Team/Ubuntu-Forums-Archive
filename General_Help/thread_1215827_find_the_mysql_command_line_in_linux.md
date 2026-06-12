---
title: "find the mysql command line in linux"
date: 2009-07-17
forum: General Help
---

### Post by roquin on 2009-07-17
Hi, guys. Im setting up apache server  with mysql  in ubuntu 9.04  and i want to use mysql command line but i do not know how to get access to it. does some now knows how?  i would appreciate it thanks

---

### Post by FluffyElmo on 2009-07-17
Not sure about Edubuntu but in regular Ubuntu you just open a terminal and type the command there. Mysql will be placed in your path when it's installed. The basic command would be:

```
mysql -u username -p
```

By default your Mysql *username* will be *root* and there will be no password. Type *\q;* and hit enter to exit back to the regular command prompt.

---

