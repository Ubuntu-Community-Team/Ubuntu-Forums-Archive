---
title: "problem with libpng"
date: 2012-04-10
forum: General Help
---

### Post by Meijuh on 2012-04-10
Hi,

I am trying to install a program using wine, but it reports I am missing libpng12.so.0.

```
err:wincodecs:PngEncoder_CreateInstance Failed writing PNG because unable to find libpng12.so.0

```

However, it does seem the package is installed:
```
sudo apt-get install libpng12-0
``` results in ```
libpng12-0 is already the newest version.
```

Any idea what I am missing here?

---

### Post by kazztan0325 on 2012-04-11
Hi Meijuh,

What version of Ubuntu are you using?
And its architecture is 32 bit?, or 64 bit?

I guess possibly you would need to install not only 'libpng12-0' but also 'ia32-libs' if you are using 64 bit Ubuntu, because I found following information.

**>> Ubuntu >> Packages >> Package Contents Search Results**
[http://packages.ubuntu.com/search?suite=oneiric&arch=any&mode=exactfilename&searchon=contents&keywords=libpng12.so.0]("http://packages.ubuntu.com/search?suite=oneiric&arch=any&mode=exactfilename&searchon=contents&keywords=libpng12.so.0")

---

### Post by Meijuh on 2012-04-11
Hi, I am using ubuntu 11.10 64 bit.
I have installed ia32-libs. When I do locate libpng12.so.0:

```
$ locate libpng12.so.0
``` I get:

```
/lib/i386-linux-gnu/libpng12.so.0
/lib/i386-linux-gnu/libpng12.so.0.46.0
/lib/x86_64-linux-gnu/libpng12.so.0
/lib/x86_64-linux-gnu/libpng12.so.0.46.0
/lib32/libpng12.so.0
/lib32/libpng12.so.0.46.0
/usr/lib/libpng12.so.0
/usr/lib/x86_64-linux-gnu/libpng12.so.0
/usr/lib32/libpng12.so.0
```

Why can't wine find libpng12.so.0?

---

### Post by kazztan0325 on 2012-04-11
> **Meijuh said:**
> Why can't wine find libpng12.so.0?

Hmm..., it is strange...
Sorry, I also have no idea at present.

Does anyone know how to solve @Meijuh's wine problem?

---

