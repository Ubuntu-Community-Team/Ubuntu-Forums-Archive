---
title: "libglib-2.0.la and other"
date: 2012-06-17
forum: General Help
---

### Post by sosroot on 2012-06-17
Why libglib-2.0.la and others are missing from 12.04 LTS ? These files are needed for example for compiling EFL libraries.

---

### Post by MG&amp;TL on 2012-06-17
> **sosroot said:**
> Why libglib-2.0.la and others are missing from 12.04 LTS ? These files are needed for example for compiling EFL libraries.

...if you mean ELF libraries, I doubt it. You don't need anything but an assembler to make an ELF library AFAIK.

And libglib2.0 is available. If you want the header files, you want the package *libglib2.0-dev*.

---

### Post by sosroot on 2012-06-17
> **MG&TL said:**
> ...if you mean ELF libraries, I doubt it. You don't need anything but an assembler to make an ELF library AFAIK.

And libglib2.0 is available. If you want the header files, you want the package *libglib2.0-dev*.

I mean Enlightenment Foundation Libraries for enlightenment.  Whereas in 11.20 libglib-2.0.la exists in /usr/lib/x86_64-linux-gnu / it disappeared in version 12.04. This file (and others of same type) is required to compile some  EFL libraries.

---

### Post by MG&amp;TL on 2012-06-17
Well, it may be a bug, or you could do something like as suggested here: [http://askubuntu.com/questions/7990/what-can-i-do-about-missing-libgdk-pixbuf-2-0-la](http://askubuntu.com/questions/7990/what-can-i-do-about-missing-libgdk-pixbuf-2-0-la)

...sorry about earlier post, not familiar with enlightenment libraries. :)

---

