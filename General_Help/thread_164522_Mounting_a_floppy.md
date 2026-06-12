---
title: "Mounting a floppy"
date: 2006-04-22
forum: General Help
---

### Post by brentmd on 2006-04-22
I have a diskette with information that i need.  I have used commands found on the internet but none seem to work.

I get this error when trying to load the floppy,

Unable to mount the selected volume.:
Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount

Mounting is vrey new to me so help would be appreciated!:KS

---

### Post by IYY on 2006-04-22
Try this:

```
mount /dev/fd0
```

---

### Post by brentmd on 2006-04-22
That code seems to work to a point but after the grinding stopps i get this errer

mount: you must specify the filesystem type

Any suggestions?

---

### Post by IYY on 2006-04-22
[QUOTE=brentmd]That code seems to work to a point but after the grinding stopps i get this errer

mount: you must specify the filesystem type

Any suggestions?[/QUOTE]

How about

```
mount -t vfat /dev/fd0
```

---

