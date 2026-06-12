---
title: "creating an iso with dd (when to set blocks?)"
date: 2009-08-20
forum: General Help
---

### Post by PGScooter on 2009-08-20
Hi, when making an iso from a dvd or cd with dd, when should I set the block size? Some suggestions I have seen say simply:
```
dd if=/dev/cdrom of=isofile
```, others specify a block size (commonly 1024 if I remember).

Thank you

---

### Post by Gen2ly on 2009-08-20
PGScooter, I've seen people set block size but I think the default (1024?) is just fine.  I do this all the time as per your command above and never had a problem with it.

---

### Post by djurny on 2009-08-20
the 'blocksize' parameter you mean here is the size of blocks to be read (and/or written) by dd itself..
leave it at default, unless you're writeing to something you know that has a maximum blocksize (e.g. usb sticks)..

---

