---
title: "Where do I browse disks?"
date: 2009-09-13
forum: General Help
---

### Post by Clove7 on 2009-09-13
Like my hard drives, CD drives etc. Where do I browse them, or get to them from ubuntu (or kubuntu). I can't figure out where it is.

---

### Post by jmszr on 2009-09-13
Clove7,

In Ubuntu try Places > Computer .

---

### Post by Clove7 on 2009-09-13
> **jmszr said:**
> Clove7,

In Ubuntu try Places > Computer .
That's gnome, I'm running KDE I.E. kubuntu :(.

---

### Post by j7%&lt;RmUg on 2009-09-13
Open a Konsole and type:

cd /

This takes you to the root of the file system, you should be able to explore from there.(just dont delete anything!)

---

### Post by Clove7 on 2009-09-13
> **nisshh said:**
> Open a Konsole and type:

cd /

This takes you to the root of the file system, you should be able to explore from there.(just dont delete anything!)
I'm talking about my drives. . .disks, etc. I don't see any drives or disks in there. What is the path called? I thought it was system: or something in konqueror.

---

### Post by lidex on 2009-09-14
Try using Konquerer - or Dolphin. Should be in your menu somewhere.

---

### Post by Clove7 on 2009-09-14
> **lidex said:**
> Try using Konquerer - or Dolphin. Should be in your menu somewhere.
Dang, couldn't find it at all :(.

---

### Post by t0p on 2009-09-14
I don't know what the dolphin icon looks like (I'm a gnome user).  But if you open a konsole and type in the command

```
dolphin
```

then dolphin should open in a new window.

---

### Post by P4man on 2009-09-14
> **Clove7 said:**
> Dang, couldn't find it at all :(.

Im guessing you are looking for a C: and D: and E: drive?
There is no such thing in linux. Everything is a folder.

The closest thing to a "c:" drive would be "/" (root).
Your "E: cdrom" will probably be in "/media/cdrom"
Another harddrive could be mounted in "/media/externaldrive"

---

