---
title: "Compilation error while installing PolyJ"
date: 2011-08-08
forum: General Help
---

### Post by awhawh on 2011-08-08
Dear Forum-members,
[U]
Ubuntu version[/U]:

 ```

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:    10.04
Codename:    lucid

```_Aim:_ 
I want to install PolyJ ([http://www.pmg.csail.mit.edu/polyj/](http://www.pmg.csail.mit.edu/polyj/))

_Output:_ 
The command './configure' delivers the following output:
```

loading cache ./config.cache
Target is UNIX platform
checking for javac... (cached) javac
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -g -I. -I.. -I$(srcdir)/../common ) works... yes
checking whether the C compiler (gcc -g -I. -I.. -I$(srcdir)/../common ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for AIX... no
checking for POSIXized ISC... no
checking for minix/config.h... (cached) no
checking for c++... (cached) c++
checking whether the C++ compiler (c++ -g -O2 ) works... yes
checking whether the C++ compiler (c++ -g -O2 ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking for ranlib... (cached) ranlib
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether ln -s works... (cached) yes
checking for flex... (cached) lex
checking for yywrap in -ll... (cached) no
checking for makedepend... no
checking for sh... (cached) /bin/sh
checking for gmake... (cached) /usr/bin/make
checking MAKEFLAGS... -$(MAKEFLAGS)
checking for main in -lstdc++... (cached) yes
checking for main in -lm... (cached) yes
checking for head... (cached) yes
checking for sed... (cached) yes
checking polyj version... 1.0.2
checking for dirent.h that defines DIR... (cached) yes
checking for opendir in -ldir... (cached) no
checking how to run the C++ preprocessor... (cached) c++ -E
checking for ANSI C header files... (cached) yes
checking for unistd.h... (cached) yes
checking for ieeefp.h... (cached) no
checking for std/bastring.cc... (cached) no
checking whether we must explicitly instantiate unicode_string::nilRep... (cached) yes
checking for working alloca.h... (cached) no
checking for alloca... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... (cached) yes
checking for working mmap... (cached) no
checking for sysctl... (cached) yes
checking for strtol... (cached) yes
checking for isinf... (cached) yes
checking for isnan... (cached) yes
checking for copysign... (cached) yes
checking for finite... (cached) yes
checking whether /usr/bin/make sets ${MAKE}... (cached) yes
checking whether byte ordering is bigendian... (cached) no
checking size of char... (cached) 1
checking size of short... (cached) 2
checking size of int... (cached) 4
checking size of long... (cached) 4
checking size of long long... (cached) 8
checking whether we are using gcc<=2.7... (cached) no
checking whether ios::binary works... no
creating ./config.status
creating Makefile
creating guavac/Makefile
creating guavac/common/Makefile
creating guavac/compiler/Makefile
creating guavac/config.h
guavac/config.h is unchanged

```The command 'make' delivers the following output:
```

make[1]: Entering directory `/home/ah/Backup/PolyJ/polyj-1.0.2/guavac'
for d in common compiler; do                              \
      echo making all in $d;                          \
      (cd $d && make all) || exit 1;                      \
    done
making all in common
make[2]: Entering directory `/home/ah/Backup/PolyJ/polyj-1.0.2/guavac/common'
make -w -f Makefile -f defaultdep.mk .objects;
make[3]: Entering directory `/home/ah/Backup/PolyJ/polyj-1.0.2/guavac/common'
c++ -g -I. -I.. -I./../common -I.  -c JavaAttribute.C
In file included from JavaConstant.h:7,
                 from JavaClassFile.h:7,
                 from JavaAttribute.h:8,
                 from JavaAttribute.C:5:
unicode_string.h:36: error: &#8216;string_char_traits&#8217; was not declared in this scope
unicode_string.h:36: error: template argument 2 is invalid
unicode_string.h:36: error: expected &#8216;{&#8217; before &#8216;>&#8217; token
unicode_string.h:36: error: expected unqualified-id before &#8216;>&#8217; token
In file included from JavaClassFile.h:8,
                 from JavaAttribute.h:8,
                 from JavaAttribute.C:5:
JavaFieldInfo.h:5: error: expected declaration before end of line
make[3]: *** [JavaAttribute.o] Error 1
make[3]: Leaving directory `/home/ah/Backup/PolyJ/polyj-1.0.2/guavac/common'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ah/Backup/PolyJ/polyj-1.0.2/guavac/common'
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/ah/Backup/PolyJ/polyj-1.0.2/guavac'
make: *** [subdirs] Error 1

```_Question:_
How do I resolve the error in the beforementioned output: "unicode_string.h:36: error: &#8216;string_char_traits&#8217; was not declared in this scope"?

Thank you in advance for your help. Any suggestions are appreciated.

---

