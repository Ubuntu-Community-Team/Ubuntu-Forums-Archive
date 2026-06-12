---
title: "xauth add not permanent?"
date: 2010-03-30
forum: General Help
---

### Post by FREEZX on 2010-03-30
I want to add ane entry in my xauth. i use these comands:
```
freezx@freezx-desktop:~$ xauth
Using authority file /tmp/.gdm4VHEAV
xauth> list
freezx-desktop/unix:0  MIT-MAGIC-COOKIE-1  daea59dbca194bd9f98f038efc6fd6e9
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  daea59dbca194bd9f98f038efc6fd6e9
xauth> add :1.0 MIT-MAGIC-COOKIE-1  daea59dbca194bd9f98f038efc6fd6e9
xauth> list
freezx-desktop/unix:0  MIT-MAGIC-COOKIE-1  daea59dbca194bd9f98f038efc6fd6e9
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  daea59dbca194bd9f98f038efc6fd6e9
freezx-desktop/unix:1  MIT-MAGIC-COOKIE-1  daea59dbca194bd9f98f038efc6fd6e9
xauth> exit
Writing authority file /tmp/.gdm4VHEAV

```so the config is saved. Bit when i restart all the cookie values are changed and the new entry is gone. How can i make this entry permanent?

---

### Post by FREEZX on 2010-03-31
bump

---

### Post by paolini on 2010-06-18
Hi, maybe a little late, but ...

The gdm reset the .Xauthority every time it starts.
So you must include the code to add this cookie in the script that creates the display :1
Take a look at the /usr/bin/startx, for example, where there is a line like that 
```
xauth add $displayname . $mcookie 
```

---

