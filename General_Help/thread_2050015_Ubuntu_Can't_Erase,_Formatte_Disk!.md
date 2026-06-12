---
title: "Ubuntu Can't Erase, Formatte Disk!"
date: 2012-08-29
forum: General Help
---

### Post by HoCo xXSamXx on 2012-08-29
Ok, So I am trying to erase everything off a CD ( I burned the wrong .ISO :/ ) And I have tried Brasero, wich doesnt recognize a disk when I use the tools>blank... and I have tried terminal:
```
umount /dev/cdrom

cdrecord dev=/dev/cdrom blank=fast
```
And I get an error. Any ideas guys?

---

### Post by Ms. Daisy on 2012-08-29
What kind of CD is it? read/write? read only?

---

### Post by Mark Phelps on 2012-08-30
> **HoCo xXSamXx said:**
> Ok, So I am trying to erase everything off a CD ...

You can't actually "erase" a CD like you can a folder on a drive.  If the CD is an RW type (rewriteable), you can reset it -- but you have to do that in a CD burning app.

---

