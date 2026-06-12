---
title: "KDE headers"
date: 2006-04-12
forum: General Help
---

### Post by Mau on 2006-04-12
I'm trying to compile kasablanca (if anyone knows of a deb package, let me know), but I am running into trouble when it asks for the KDE headers.

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```

I have tried specifying them to /usr/kde3/, /etc/kde3/ and a few others, but they all fail.  Where can I find the KDE headers?  It seems that the Kubuntu packagers have changed the locations of some things.

---

### Post by Al3xanR0 on 2006-04-13
[QUOTE=Mau]I'm trying to compile kasablanca (if anyone knows of a deb package, let me know), but I am running into trouble when it asks for the KDE headers.

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```

I have tried specifying them to /usr/kde3/, /etc/kde3/ and a few others, but they all fail.  Where can I find the KDE headers?  It seems that the Kubuntu packagers have changed the locations of some things.[/QUOTE]

To locate headers type

```
find / -name kapplication.h
```

you should you get the followng output:

```
/usr/include/kde/kapplication.h
```

If not do the type the following:

```
apt-get install kdebase-dev 
```

(which contains the necessary header file as noted above)

Hope this helps

---

### Post by Mau on 2006-04-13
Great!  That worked.

What are -dev packages?  I was under the impression that it was the source code.

---

### Post by az on 2006-04-13
[QUOTE=Mau]Great!  That worked.

What are -dev packages?  I was under the impression that it was the source code.[/QUOTE]
The source code is all of the code.  Once you compile c or c++ code into binary form, you need headers to tell you what functions the binary uses.  This is how proprietary binary-only software is distributed - you get the headers to be able to use the object files.  

To be able to compile something to use with precompiled binaries, you just use their headers.  So it *is* a part of the source code, but only a small and specific portion of it.

---

### Post by gingermark on 2006-04-13
[QUOTE=Mau]I'm trying to compile kasablanca (if anyone knows of a deb package, let me know)[/QUOTE]
Sorry if this is too late, but you can get Kasablanca in [MaXeR's Repository](http://repos.knio.it/). The details for the Breezy repository are down near the bottom of the page.

---

### Post by Mau on 2006-04-13
Yes, using apt is much easier.  I was trying to build it, but whenever I would build it, I could never find it!  Working now.

---

### Post by Al3xanR0 on 2006-04-14
[QUOTE=Mau]Great!  That worked.

What are -dev packages?  I was under the impression that it was the source code.[/QUOTE]

:D glad that worked for you.

---

