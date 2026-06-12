---
title: "How to open/extract *.iso file on Ubuntu gnome?"
date: 2006-01-21
forum: General Help
---

### Post by Zlatan on 2006-01-21
thank you

---

### Post by cbudden on 2006-01-21
Right click -> Extract here.

---

### Post by aysiu on 2006-01-21
Why do you want to extract an ISO? I'm just curious. Most of the time people want to burn it.

---

### Post by Foucault on 2006-01-21
You can also mount it!
Try:
```

mkdir ~/mount_dir
sudo mount -o loop myIso.iso ~/mount_dir

```

Then you can explore it as you could explore a directory or a cdrom.

---

### Post by qball on 2006-01-21
A very linux like solution to read (even write) the files of an .iso file is:

mount -o loop isofile.iso /media/cdrom/

This will mount the iso over the loopback on /media/cdrom/
if you want you can even write to it. (but don't forget to umount).

---

### Post by Zlatan on 2006-01-29
thank you

---

### Post by maxdevis on 2006-01-29
hmmm,

i made some iso by myself.
it are dvd's.
but when i mount it, i can acces the files, but i cant play the dvd by clicking on it in Totem.
and now my dvd-drive doesn't do it anymore.

---

