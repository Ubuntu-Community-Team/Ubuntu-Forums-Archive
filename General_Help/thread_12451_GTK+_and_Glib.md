---
title: "GTK+ and Glib"
date: 2005-01-24
forum: General Help
---

### Post by python on 2005-01-24
I am wrestling to install glib and was wondering. Is it possible with apt-get or dkpg? I have been playing with them but I was wondering if there is an easy method to install it.

---

### Post by mendicant on 2005-01-24
apt-get install libglib2.0-dev maybe?  There's also the debug version libglib2.0-dbg and the 1.2 version.  Personally, I prefer to use aptitude:

aptitude install libglib2.0-dev, which keeps better track of automatically installed packages.

---

### Post by python on 2005-01-25
Nice one cheers. Yeah, aptitude does seem better ;-)

---

