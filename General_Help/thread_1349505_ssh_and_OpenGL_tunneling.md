---
title: "ssh and OpenGL tunneling"
date: 2009-12-08
forum: General Help
---

### Post by godlike_panos on 2009-12-08
Im trying to view a basic OpenGL application (glxgears) through ssh but I get this error:

```
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
glxgears: ../../src/xcb_io.c:542: _XRead: Assertion `dpy->xcb->reply_data != ((void *)0)' failed.
Aborted
```

I execute ssh with X11 forwarding and compression:

```
ssh -X -C user@host
```


Does anyone knows why I get this error and how to correct it?

Im using Ubuntu 9.10 64bit with an ATI 4870 and using fglrx provided by the repositories.


Thanks in advance!

---

### Post by godlike_panos on 2009-12-14
Anyone?

---

