---
title: "INstalling fonts."
date: 2009-07-29
forum: General Help
---

### Post by sthrnpagan on 2009-07-29
How does one install a font? I can not figure it out. Any help would be appreciated. thanks in advance

---

### Post by blazemore on 2009-07-29
As root, copy the files to /usr/share/fonts

```
sudo cp /path/to/font /usr/share/fonts
```

---

### Post by pmlxuser on 2009-07-29
if you just want to have the fonts for your self creat a folder in your home directory

.fonts
ie
```


username@user-linux $ mkdir .fonts


```
put all the fonts in there log out log in viola.

---

### Post by kostkon on 2009-07-29
In simple words:

go to your home folder, select *View &#8594; Show Hidden Files* in Nautilus and you should see the *.fonts* folder. Put your fonts in there.

If the folder does not exist, then just create it yourself.

The fonts will become available right away.

---

