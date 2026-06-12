---
title: "Failing make command after ./configure completes"
date: 2011-03-21
forum: General Help
---

### Post by MaxReality on 2011-03-21
Hello Everyone,

I'm new to the forums and I'm also new to Ubuntu 10.10. I'm having trouble compiling modutils-2.4.27 from the source code. 

Here's a little background information: 

I'm using linux kernel 2.6.35-28-generic

I'm trying to install the Intel 855gm chipset drivers which (I found out through a lot of research) requires a linux kernel 2.4.x.x module.

I've downloaded the source code for the 2.4.37.11. 

I've used ver_linux to confirm I have the necessary packages for the kernel.

When Linux attempts to create the .deb module for /lib/modules it fails stating: /bin/sh: /sbin/genksyms: not found

Through more research I found out that genksyms is bundled with modutils-2.4.27. Also, I was told it should be bundled with module-init-tools which works better with kernel 2.6.x.x

I have module-init-tools installed through the Synaptic Package Manager but genksyms is still missing from the /sbin directory

Whats Happening Now?
Once I downloaded modutils-2.4.27.tar.gz. I attempted to compile the source code:

./configure completed successfully with the output:

bash:~/Downloads/modutils-2.4.27$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking whether ln -s works... yes
checking for wordexp... yes
checking for glob... yes
checking whether R_X86_64_NONE is declared... yes
checking for query_module in -lc... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Makefile.common
config.status: creating depmod/Makefile
config.status: creating genksyms/Makefile
config.status: creating insmod/Makefile
config.status: creating obj/Makefile
config.status: creating util/Makefile
config.status: creating man/Makefile
bash:~/Downloads/modutils-2.4.27$

Once CONFIGURE completed successfully, I tried using the MAKE command to compile the source into binary for installation and here is the output:

bash:~/Downloads/modutils-2.4.27$ make
make[1]: Entering directory `/home/rick/Downloads/modutils-2.4.27/util'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/rick/Downloads/modutils-2.4.27/util'
make[1]: Entering directory `/home/rick/Downloads/modutils-2.4.27/obj'
gcc  -O2 -Wall -I./../include -D_GNU_SOURCE -DPACKAGE_NAME=\"\"  -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\"  -DPACKAGE_BUGREPORT=\"\" -DCONFIG_ROOT_CHECK_OFF=0   -DCOMMON_3264  -DELF_MACHINE_H='"elf_i386.h"' -DARCH_i386 -DONLY_32 -c -o  obj_kallsyms.o obj_kallsyms.c
In file included from obj_kallsyms.c:26:
./../include/util.h:42: warning: built-in function ‘log’ declared as non-function
obj_kallsyms.c: In function ‘obj32_kallsyms’:
obj_kallsyms.c:204: error: lvalue required as left operand of assignment
obj_kallsyms.c:279: error: lvalue required as left operand of assignment
make[1]: *** [obj_kallsyms.o] Error 1
make[1]: Leaving directory `/home/rick/Downloads/modutils-2.4.27/obj'
make: *** [all] Error 2
bash:~/Downloads/modutils-2.4.27$

I'm not sure why I'm receiving this error. I'm not even sure what Error 2 is describing. Any help would be awesome! please let me know if you need anymore information or if I've posted in the wrong place.. :p

---

