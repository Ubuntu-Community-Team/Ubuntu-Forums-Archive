---
title: "Problem Cross-compiling with toolchain"
date: 2009-07-02
forum: General Help
---

### Post by Isellsigals on 2009-07-02
Im trying to cross-compile ircd-hybrid on my ubuntu box for power-pc architecture.

Everything goes well apart from it does not detect OpenSSL library... I specified where it is installed in the ./configure but it still does not detect it; the strange thing is that when I compile it using gcc that came with ubuntu it DOES detect it so I'm at a loss as to why it is not seeing the OpenSSL library using toolchain and am hoping someone could shed some light.

```
CC=/tmp/eee/powerpc-linux/bin/powerpc-linux-gcc
LD=/tmp/eee/powerpc-linux/bin/powerpc-linux-ld
RANLIB=/tmp/eee/powerpc-linux/bin/powerpc-linux-ranlib
CFLAGS="-I/tmp/eee/powerpc-linux/include"
LDFLAGS="-L/tmp/eee/powerpc-linux/lib"

./configure --enable-openssl=/usr/local --host=powerpc-unknown-linux --target=powerpc-unknown-linux --build=i686-pc-linux --prefix=/tmp/eee/dist

```With gcc ubuntu:
> Checking for OpenSSL... /usr/local
Checking for OpenSSL 0.9.6 or above... foundtoolchain power-pc:
> Checking for OpenSSL... /usr/local
Checking for OpenSSL 0.9.6 or above... no - OpenSSL support disabled

---

### Post by chaospike on 2009-08-21
try installing libssl or libssl0.9.x via apt-get; this is not a dependency of OpenSSL install.

---

