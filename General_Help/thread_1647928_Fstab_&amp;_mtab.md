---
title: "Fstab &amp; mtab"
date: 2010-12-18
forum: General Help
---

### Post by Linyx on 2010-12-18
[SIZE="2"]Well, i had Google it first, and i read somewhat about these both,and i Got that, In Fstab >We can manage our Drives(Which will be mounted at Boot-time) but I didn't understand MTAB, I have read that in MTAB >Only-Mounted Drives appears...[/SIZE]

[SIZE="2"]The things i want to know is...[/SIZE]

[SIZE="2"]Can we Edit mtab ? And What will be the reason for editing Mtab..?[/SIZE]

[SIZE="2"]Just as we Edit FSTAB for some Reason Like Auto-mounting, so what about Mtab...? i means its **Editing Benefits**...?[/SIZE]

---

### Post by Linyx on 2010-12-18
[SIZE="2"]bump[/SIZE]

---

### Post by oldfred on 2010-12-18
You do not edit mtab, but if you edit fstab you should always run this to make sure you have edited correctly and I believe it then has updated mtab.

```
sudo mount -a
```

It will either return to command line, with you changes now being used or tell you what is wrong.

---

### Post by Linyx on 2010-12-18
[SIZE="2"]Thanks for that:p, I just want to know that what will be the Benefit of Editing MTAB,is their any Usage of it, like,we have FSTAB > For Auto-mounting ....[/SIZE]

---

### Post by psusi on 2010-12-18
You can not edit mtab.  It is used by mount to keep track of what filesystems you currently have mounted.  You do not touch it directly.

---

### Post by WorMzy on 2010-12-18
mtab is managed by the system, it just keeps a list of the mounted filesystems so that if you run "mount -a", it won't try to mount filesystems which are already mounted (as this would result in an error). It is also used by some applications to list which partitions are mounted, and with which options, e.g. "mount -l".

Editing mtab serves no purpose, and may cause errors, so the best advice is to just leave it alone. :)

---

### Post by Linyx on 2010-12-18
[SIZE="2"]Thanks to Both, i GOt it :p[/SIZE]

---

