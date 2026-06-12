---
title: "External HD Problem"
date: 2010-06-03
forum: General Help
---

### Post by mkurtism on 2010-06-03
My external was working and was copying, but froze up in the middle of a transfer and now it tells me that it cannot mount it.  Running ubuntu 10.4

Tried to walk myself through it, but i'm not smart enough.  Help please?

---

### Post by bumanie on 2010-06-03
Put this command in terminal with the external hard drive plugged in but ensuring it is not mounted. It will do a filesystem check and fix errors if it can. Remember to name the device correctly, by changing the xx to the drive letter & number. > sudo e2fsck -C0 -p -f -v /dev/sdxx

---

### Post by mkurtism on 2010-06-03
No dice. It tells me i'm not authorized

---

