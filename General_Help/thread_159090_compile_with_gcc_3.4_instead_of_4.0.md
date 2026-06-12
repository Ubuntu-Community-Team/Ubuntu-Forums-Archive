---
title: "compile with gcc 3.4 instead of 4.0"
date: 2006-04-12
forum: General Help
---

### Post by leftyman on 2006-04-12
Hello:

I have downloaded source for a program called qemu (they dont have binaries for AMD64)


when I tyoe ./configure I receive this warning:

"QEMU is known to have problems when compiled with gcc 4.x
It is recommended that you use gcc 3.x to build QEMU"

I have both compilers installed (3.4 and 4.0)

Is it possible to force a ./configure using 3.4 version of Ggcc?


thanks

---

### Post by Darkriser on 2006-04-12
sudo CC=gcc-3.4
sudo export CC

(type in console, of course)

---

### Post by armware on 2006-08-25
hiya, i'm in the same boat.
i run the above and get:

sudo: CC=gcc-3.4: command not found

running without sudo does seem to work, but then i have to run the export command without sudo, then the ./configure fails with the same message as before.

---

### Post by armware on 2006-08-25
after poking around in the configure file, i found that running:
./configure -cc=gcc-3.4
works.

---

