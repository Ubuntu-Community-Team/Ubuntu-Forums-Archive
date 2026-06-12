---
title: "need more information from lsusb"
date: 2009-12-08
forum: General Help
---

### Post by SIGTERMer on 2009-12-08
Hello everyone

Does anyone know how to get more information on usb devices. lsusb only lists vendor/product ids which is not enough. I need the serial number.

Thanks

---

### Post by Zorael on 2009-12-08
Even with -v?

```
$ sudo lsusb -v
```

---

### Post by hal10000 on 2009-12-08
A little more information:
```
lsusb -v
```
Much more information:
```
lsusb -vv
```
Very much more information:
```
lsusb -vvv
```

---

### Post by SIGTERMer on 2009-12-08
don't know how i missed that one.
thanks everyone.

---

