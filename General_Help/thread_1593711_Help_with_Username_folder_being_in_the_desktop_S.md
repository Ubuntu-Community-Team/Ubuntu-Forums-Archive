---
title: "Help with Username folder being in the desktop :S"
date: 2010-10-11
forum: General Help
---

### Post by ilogiikzv0 on 2010-10-11
Allright, I was experimenting with ubuntu 10.10, im a newbie.
This is what happened,
I wanted to make a shortcut of places tab on the desktop, but the places tab MOVED to the desktop, having simultaneous folders of home on the desktop and in computer.

here is a pic
[[IMG=http://img684.imageshack.us/img684/2454/screenshotlte.png][/IMG]]("http://img684.imageshack.us/i/screenshotlte.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")
I want to delete those folders from the desktop without deleting them. its weird to explain.
I tried copying to the home folder but it says cannot replace itself, but those folders are on the desktop.

Thanks

---

### Post by ilogiikzv0 on 2010-10-14
bump

its an easy question, come on. I have searched but i do not know what terms to use.
basically its like the (music,documents, etc.) folders are simultaneously on the "username" folder and in the desktop, look at the pic i attached before to see what i mean.

thanks in advance, im a newbie

btw, this is ubuntu 10.10

---

### Post by Morbius1 on 2010-10-14
In a terminal:
```
gconf-editor
```
Go to /apps/nautilus/preferences/desktop_is_home_dir

If it's checked - unchek it.

---

### Post by ilogiikzv0 on 2010-10-16
> **Morbius1 said:**
> In a terminal:
```
gconf-editor
```Go to /apps/nautilus/preferences/desktop_is_home_dir

If it's checked - unchek it.

Thank you, that solved it :)

---

