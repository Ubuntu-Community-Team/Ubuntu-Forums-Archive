---
title: "How can I fix ls sort order? (asciibetical, command line)"
date: 2009-08-20
forum: General Help
---

### Post by blot on 2009-08-20
How can I fix the sorting order that's used by `ls` in my terminal? It's not displaying names in asciibetical order. Instead, it's mixing the uppercase and lowercase together.

Thanks.

---

### Post by Copernicus1234 on 2009-08-20
Per default, if two files have the same name, where one has capital letters and the other does not, it seems to list it as: 

example
Example

And you want it the other way around, right?

Not sure if there is a way. Dont think there is a flag for it anyways. You can always script it. :)

---

### Post by blot on 2009-08-20
> And you want it the other way around, right?

No. When I run an `ls -l` (or `ls -1`), I want all the files like README, LICENSE, COPYING, Changes, and TODO listed before (above) files/directories like foo.py, lib, and test. This is the standard way `ls` has always worked for me in GNU/Linux, Mac OS X, and FreeBSD.

It appears that maybe Ubuntu changed this on purpose, and I want to fix it and change it back.

---

### Post by blot on 2009-08-20
Just discovered this:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=816753](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=816753)

Will give it a try later.

---

