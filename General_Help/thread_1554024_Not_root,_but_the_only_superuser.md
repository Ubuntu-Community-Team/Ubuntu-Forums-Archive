---
title: "Not root, but the only superuser"
date: 2010-08-16
forum: General Help
---

### Post by tmandpea on 2010-08-16
Hey. So I'm trying to install the icon package called Token-Dark. I figured out that I have to move the icons to usr/share/icons. When I try to copy the file I get the error "permission denied". I tried to change the permissions on the folder, but it says that I'm not the root, or the owner of the files, so I can't change anything.

The weird thing is that I'm the superuser, and the only user on the machine. Help! :confused:

I'm running 10.04 Ubuntu 64 bit.

---

### Post by lisati on 2010-08-16
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tmandpea on 2010-08-16
alright well how would I move the folder over then?

---

### Post by wojox on 2010-08-16
Try opening your Home Folder and showing hidden files (Ctrl+H)

Drag and drop you .tar.gz package in there and then extract it:

Right click and choose extract here.

System > Preferences > Appearance > Theme > Customize

---

### Post by tmandpea on 2010-08-16
alright, would that work if it's not a .gz compressed file? the icons are .zip

---

### Post by wojox on 2010-08-16
> **tmandpea said:**
> alright, would that work if it's not a .gz compressed file? the icons are .zip

It should.

---

### Post by tmandpea on 2010-08-16
alright thanks, sorry for the stupid question, but not much else has been going too well soo...

---

### Post by tmandpea on 2010-08-16
alright so here's the problem though. I can uncompress the icons and everything, but when I try to drag and drop them to usr/share/icons, I can't... How do I fix this. This, I think, is the only way I can get the icons to show up when I go into customize in system preferences

---

### Post by wojox on 2010-08-16
There are no stupid questions. :)

---

### Post by wojox on 2010-08-16
> **tmandpea said:**
> alright so here's the problem though. I can uncompress the icons and everything, but when I try to drag and drop them to usr/share/icons, I can't... How do I fix this. This, I think, is the only way I can get the icons to show up when I go into customize in system preferences

Open a terminal and try

```
gksudo nautilus
```

It should let you do it then.

---

### Post by tmandpea on 2010-08-16
alright! I can move the folders into the right place!...but I can't select the icons. Does anyone know how to install custom icons? or should I make a new thread?

---

### Post by wojox on 2010-08-16
> **tmandpea said:**
> alright! I can move the folders into the right place!...but I can't select the icons. Does anyone know how to install custom icons? or should I make a new thread?

Did you try my icons in your Home Folder ?

---

