---
title: "Help building ATLAS"
date: 2010-10-03
forum: General Help
---

### Post by stair314 on 2010-10-03
I'm trying to build ATLAS on Ubuntu 10.04. The standard packages don't seem to run very fast on my machine, so I need to build from source. Unfortunately, I get this error:


~/Libraries/ATLAS3.9.25/build2$ ../configure -Fa alg -fPIC --with-netlib-lapack=/home/stair314/Libraries/lapack-3.1.1/lapack_LINUX.a
make: `xconfig' is up to date.
./xconfig -d s /home/ia3n/Libraries/ATLAS3.9.25/build2/../ -d b /home/stair314/Libraries/ATLAS3.9.25/build2  -Fa alg -fPIC --with-netlib-lapack=/home/stair314/Libraries/lapack-3.1.1/lapack_LINUX.a

ERROR around arg 10 (--with-netlib-lapack=/home/stair314/Libraries/lapack-3.1.1/lapack_LINUX.a).
USAGE: ./xconfig [flags] where flags are:
...

I asked about this on ATLAS's sourceforge site too, but I figured it was worth checking this list to see if any of you have had this problem / know of a workaround.

---

### Post by stair314 on 2010-10-08
If anyone else has the same problem later on, I managed to fix it myself.

In newer versions of ATLAS, the correct flag is:

--with-netlib-lapack-tarball

For some reason, ATLAS ships with an incredibly outdated INSTALL.TXT that you are meant to ignore. A few subdirectories down into the ATLAS directory there is a pdf with the real instructions.

---

### Post by m.vejmelka on 2011-03-11
In version 3.9.35, the relevant flag is "--with-netlib-lapack-tarfile", not "...-tarball".

---

