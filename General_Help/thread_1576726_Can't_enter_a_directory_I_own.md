---
title: "Can't enter a directory I own"
date: 2010-09-17
forum: General Help
---

### Post by wconstantine on 2010-09-17
Got a weird problem here.

```
wh1sk3yj4ck@valkyrie:~/.vmware$ ls -l
total 32
drw-rw-rw- 2 wh1sk3yj4ck wh1sk3yj4ck  4096 2010-08-05 08:06 BT4-R1
```

It would seem as if I own that dir, yea?

Well.

```
wh1sk3yj4ck@valkyrie:~/.vmware$ cd BT4-R1/
bash: cd: BT4-R1/: Permission denied

```
Enlighten me. Also, what does the '2' mean after the permissions?

---

### Post by sisco311 on 2010-09-17
> **wconstantine said:**
> 
Enlighten me. Also, what does the '2' mean after the permissions?

2 is the number of hard links to the directory, but that's fine.

Yo need execute permission (*search permission*) on the directory in order to cd into it.

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by wconstantine on 2010-09-17
That is so cool. Thanks. :)

---

### Post by sisco311 on 2010-09-17
You're welcome!

---

