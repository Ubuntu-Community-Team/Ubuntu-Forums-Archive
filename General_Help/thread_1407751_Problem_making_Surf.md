---
title: "Problem making Surf"
date: 2010-02-15
forum: General Help
---

### Post by Nosgard on 2010-02-15
Hello!

I tried to get surf ([http://surf.sourceforge.net/](http://surf.sourceforge.net/)) running on my new notebook. During ./configure i get a warning saying gtk-config cannot be found. then during make, i get an error. I am quite sure the problem is, that surf uses GTK+ 1.2, and in GTK 2.0 there is no gtk-config file.
It might be best to just do something there, but i dont know how to :/

So i tried to install GTK+ 1.2, but there i get an error (during ./configure too)
> 
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking host system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking for ranlib... (cached) ranlib
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
loading cache ./config.cache within ltconfig
ltconfig: you must specify a host type if you use `--no-verify'
Try `ltconfig --help' for more information.
configure: error: libtool configure failed

I think the problem is i am running a 64-bit xubuntu, version 9.10 and gtk 1.2. just doesnt know how to handle it.
Anyone got a clue on how to get this running?

Thanks

Jens

---

