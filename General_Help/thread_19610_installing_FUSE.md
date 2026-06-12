---
title: "installing FUSE"
date: 2005-03-12
forum: General Help
---

### Post by jey on 2005-03-12
Hi!
I searched threads about FUSE but no one matched my answer so ...

I can't get fuse working !!


```

jerome@jerome:/usr/src/modules/fuse $ uname -a
Linux jerome 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux

jerome@jerome:/usr/src/modules/fuse $ ls -ld /usr/src/kernel-headers-2.6.8-10/
drwxrwxrwx   17 root     root         4096 2005-03-12 23:24 

jerome@jerome:/usr/src/modules/fuse $ sudo ./configure --with-kernel=/usr/src/kernel-headers-2.6.8-10/
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking kernel source directory... /usr/src/kernel-headers-2.6.8-10/
checking kernel source version... 2.6.8-10
configure: creating ./config.status
config.status: creating Makefile
config.status: creating kernel/Makefile
config.status: creating lib/Makefile
config.status: creating util/Makefile
config.status: creating example/Makefile
config.status: creating include/Makefile
config.status: creating include/linux/Makefile
config.status: creating patch/Makefile
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: executing depfiles commands

``` 

After that, I have to run make.
But I get compile errors and warnings :
```

{entrée standard}: Messages de l'assembleur:
{entrée standard}:513: ERREUR: ne peut représenter le type de relocalisation BFD_RELOC_64
make[3]: *** [/usr/src/modules/fuse/kernel/dev.o] Erreur 1
make[2]: *** [_module_/usr/src/modules/fuse/kernel] Erreur 2
make[2]: quittant le répertoire « /usr/src/kernel-headers-2.6.8-10 »
make[1]: *** [all-spec] Erreur 2
make[1]: quittant le répertoire « /usr/src/modules/fuse/kernel »
make: *** [all-recursive] Erreur 1

```

Do you have an idea?
Have you installed FUSE successfully?

Many Thanks!

---

### Post by cfa on 2005-03-31
here after my fuse install script on hoary , should also work on warty :

run it as root :

    # apt-get install libssl-dev libfuse-dev fuse-utils fuse-source linux-headers-`uname -r` g++

    # cd /usr/src/ && tar jxvf fuse.tar.bz2 && cd modules/fuse/kernel
    # ./configure && make && make install && modprobe fuse

    # cd /usr/src/ && wget [http://distro.ibiblio.org/pub/linux/distributions/sorcerer/sources/rlog/1.3.6/rlog-1.3.6.tar.bz2](http://distro.ibiblio.org/pub/linux/distributions/sorcerer/sources/rlog/1.3.6/rlog-1.3.6.tar.bz2)
    # tar jxvf rlog-1.3.6.tar.bz2 && cd rlog-1.3.6 && ./configure && make && make install

    # cd /usr/src/ && wget [http://ovh.dl.sourceforge.net/sourceforge/encfs/encfs-1.2.0-2.tgz](http://ovh.dl.sourceforge.net/sourceforge/encfs/encfs-1.2.0-2.tgz)
    # tar zxvf encfs-1.2.0-2.tgz && cd encfs-1.2.0 && ./configure && make && make install
    
then launch enfs command eg :    

    $ encfs /home/youruser/crypted_raw /home/youruser/crypted

and follow the prompt to configure it :)

---

