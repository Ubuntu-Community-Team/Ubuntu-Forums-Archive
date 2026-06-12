---
title: "my home folder contents appears in desktop"
date: 2010-06-29
forum: General Help
---

### Post by s.shawky on 2010-06-29
hello
my home folers contents like downloas , documents ....
ae displayed in desktop too
and i can't hide them
and if i delete one of them the original one will be deleted

---

### Post by Morbius1 on 2010-06-29
I guess the first thing you can check is this:

In a terminal type:
```
gconf-editor
```Now go to:  apps-->nautilus-->preferences

And look for the following item: 
```
desktop_is_home_dir
```If it's checked, uncheck it.

---

### Post by burton247 on 2010-06-29
The above should work. Just saying that Ubuntu tweak allows you to show the contents of home on the desktop, you may have enabled it there.

---

