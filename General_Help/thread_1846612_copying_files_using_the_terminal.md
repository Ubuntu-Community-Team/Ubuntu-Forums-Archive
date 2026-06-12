---
title: "copying files using the terminal"
date: 2011-09-19
forum: General Help
---

### Post by unknow04 on 2011-09-19
Hi guys, if i connect a usb how I can copy all my home folder to it using the terminal ?

---

### Post by Bodsda on 2011-09-19
> **unknow04 said:**
> Hi guys, if i connect a usb how I can copy all my home folder to it using the terminal ?

```

cp -rv ~/ /media/myusbdrive

```

You may want to look at rsync though if you want to use this duplicate as your ~/ folder

Bodsda

---

### Post by unknow04 on 2011-09-19
Doesnt work media isnt the directory where the usb is... is not the "computer" directory ?

---

