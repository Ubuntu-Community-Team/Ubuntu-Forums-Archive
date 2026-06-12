---
title: "access denied could not write"
date: 2009-11-04
forum: General Help
---

### Post by sbomb on 2009-11-04
good day,  if i'm trying to copy files or save a download to the harddrive on the kubuntu desktop.  i get a message "access denied could not write to /mnt/device/51/public/data/videos".....i have tried changing permissions and changing ownership. what have i done wrong? i read something about underprivilage user, but i'm not sure exactly to resolve this. thanks

---

### Post by alphaniner on 2009-11-04
Open a terminal and post output of

```
ls -l /mnt/device/51/public/data
```

---

### Post by sbomb on 2009-11-04
ls: cannot access /mnt/device/51/public/data: No such file or directory

---

### Post by alphaniner on 2009-11-04
Well if **/mnt/device/51/public/data** does not exist, neither does **/mnt/device/51/public/data/videos**.  Your problem seems to be something other than permissions.

---

### Post by sbomb on 2009-11-04
ok, i will do a something something to figure it out thanks. let u know

---

### Post by NoaHall on 2009-11-04
Can you do a ls /media/ ?

---

### Post by sbomb on 2009-11-04
> **NoaHall said:**
> Can you do a ls /media/ ?

the outcome is cdrom cdrom)

---

### Post by NoaHall on 2009-11-04
now try ls /mnt

---

