---
title: "compiling a driver file"
date: 2012-06-08
forum: General Help
---

### Post by bdemers on 2012-06-08
I have an after market usb to serial converter.  It has only a single file XXXX.c which is listed under a redhat folder. Nothing else provided. 

I tried a compile how to, but failed with automake.sh (not finding) or ./configure(not supplied) commands.  I have installed build-essentials, don't know where to go from there.

---

### Post by MG&amp;TL on 2012-06-09
> **bdemers said:**
> I have an after market usb to serial converter.  It has only a single file XXXX.c which is listed under a redhat folder. Nothing else provided. 

I tried a compile how to, but failed with automake.sh (not finding) or ./configure(not supplied) commands.  I have installed build-essentials, don't know where to go from there.


That seems a bit dubious...sure you obtained it in the right fashion?

Presuming you don't need any external libraries, my guess is that you just compile it, although I severely doubt that.

```
gcc XXXX.c
```

---

