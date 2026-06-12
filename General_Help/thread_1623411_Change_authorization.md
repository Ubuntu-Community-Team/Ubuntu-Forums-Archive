---
title: "Change authorization"
date: 2010-11-16
forum: General Help
---

### Post by The Eight-Bit Link on 2010-11-16
Is there a file I can edit while in the live disk to change my authority/ I need to bump up a user to admin.

---

### Post by cariboo on 2010-11-16
All you need to do is use sudo before any command eg:

```
sudo fdisk -l
```

or if it's a graphical application, press Alt-F2 and type eg:

```
gksu nautilus
```

---

### Post by sisco311 on 2010-11-16
You can boot into recovery mode and add your user to the admin group.
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

If you want to do it from the Live CD, then mount the root partition and edit the **mount/point**/etc/group file, find the line which begins with **admin** and append it with the user(s) you want to add to the admin group. Users must be separated by a comma, i.e.:
```
admin:x:119:**user1**
```
or
```
admin:x:119:**user1,user2,user3**
```


Be careful, backup the file before editing it.

---

