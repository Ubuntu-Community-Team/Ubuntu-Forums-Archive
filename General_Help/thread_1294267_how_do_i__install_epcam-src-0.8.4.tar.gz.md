---
title: "how do i  install epcam-src-0.8.4.tar.gz"
date: 2009-10-18
forum: General Help
---

### Post by starcraftmaster on 2009-10-18
hey guys
how do i install epcam-src-0.8.4.tar.gz driver ??????

contents:
makefile
changelog
folder:drivers>folder:usb>epcam.h
                          epcam.c

i tried what some else said to do and it worked but in cheese it shows a black screen
but it lists the creative pd1001 in its list

---

### Post by bruno9779 on 2009-10-18
You just have to 

- untar (extract) the content of the file
- cd to the directory
- type

```
./configure
make
makeinstall
```

and that should be it

---

### Post by 3rdalbum on 2009-10-18
Does "lsusb" actually say what chipset is used in the camera, and does that match up with what the driver is meant to work with?

Sometimes manufacturers will change the chipset but not change the model number.

---

