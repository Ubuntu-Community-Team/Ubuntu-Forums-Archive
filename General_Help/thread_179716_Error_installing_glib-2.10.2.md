---
title: "Error installing glib-2.10.2"
date: 2006-05-20
forum: General Help
---

### Post by davey.moore on 2006-05-20
I downloaded the tar.gz file, uncompressed and run ./configure, it went fine, then make, it went fine, but then i did sudo checkinstall and after going for a few seconds i got the following error at the end:

_________________________________
-- Installing /home/fmulder/Desktop/glib-2.10.2/docs/reference/glib/html/index.sgml
/bin/sh /home/fmulder/Desktop/glib-2.10.2/mkinstalldirs /usr/local/man/man1
mkdir -p -- /usr/local/man/man1
mkdir: cannot create directory `/usr/local/man': File exists
make[5]: *** [install-man1] Error 1
make[5]: Leaving directory `/home/fmulder/Desktop/glib-2.10.2/docs/reference/glib'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/fmulder/Desktop/glib-2.10.2/docs/reference/glib'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/fmulder/Desktop/glib-2.10.2/docs/reference'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/fmulder/Desktop/glib-2.10.2/docs'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/fmulder/Desktop/glib-2.10.2'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.
________________________________

I hope someone has the answer.

Thank you!

---

### Post by Ramses de Norre on 2006-05-20
Does sudo make install work? I've seen checkinstall fail on some packages..

---

