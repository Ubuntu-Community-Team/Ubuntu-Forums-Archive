---
title: "edit and save file problems in apache conf"
date: 2009-07-08
forum: General Help
---

### Post by roquin on 2009-07-08
Hi, guys, im trying to conf apache server on ubuntu 9.04 desktop. But when i want  to edit  any file and save it i get this message: You do not have the permissions necessary to save the file. does some one can help that would be great. thanks( actually this problem is also in www files)

---

### Post by ewankho on 2009-07-09
Use another user with permission to change the file or join a group that has permission to change the file.
Also, you can use sudo when editing the file.

---

### Post by credobyte on 2009-07-09
```
gksudo nautilus
```

Now, browse to wherever you need & enjoy :)

---

### Post by benh13 on 2009-07-09
open the file in terminal, beginning with gksudo gedit

---

