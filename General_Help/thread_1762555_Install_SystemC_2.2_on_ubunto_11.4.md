---
title: "Install SystemC 2.2 on ubunto 11.4"
date: 2011-05-19
forum: General Help
---

### Post by Loufa on 2011-05-19
Hello 

i am facing a peoblem in installing systemC when i try to run a patch i got the following error :
Hunk #1 FAILED at 91.
1 out of 1 hunk FAILED -- saving rejects to file Makefile.in.rej
patching file src/sysc/utils/sc_utils_ids.cpp
Hunk #1 FAILED at 58.
1 out of 1 hunk FAILED -- saving rejects to file src/sysc/utils/sc_utils_ids.cpp.rej

also for installation i got the following error:

make[3]: *** [sc_utils_ids.o] Error 1
make[3]: Leaving directory `/home/satvik/Desktop/system/src/sysc/utils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/satvik/Desktop/system/src/sysc'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/satvik/Desktop/system/src'
make: *** [all-recursive] Error 1

i tried the solns proposed in 
[http://ubuntuforums.org/showthread.php?t=1257173](http://ubuntuforums.org/showthread.php?t=1257173)

but it still not working also the patch proposed is not working 

can any one help me ??

thanks in advance.

---

### Post by rsdivekar on 2012-04-09
Pl help me: 
( I am also getting an installation error - installing systemc on ubuntu 11.10:


g++ -I. -I/home/administrator/systemc-2.2.0/include myfile.o -L. -L/home/administrator/systemc-2.2.0/lib-linux -lsystemc -lm -o myfile.o

/home/administrator/systemc-2.2.0/lib-linux/libsystemc.a(sc_main_main.o): In function `sc_elab_and_sim':
sc_main_main.cpp:(.text+0x71): undefined reference to `sc_main'
collect2: ld returned 1 exit status

All that myfile contains is:
int sc_main(int ac, char *av[])
{
return 0;
}

What could be the problem ?

---

### Post by triya on 2012-05-15
I was getting the same problems, then I tried this..

first find the following in your installation-
systemc-2.2.0/src/sysc/utils/sc_utils_ids.cpp

only one header will be included in this file, you have to add two more headers here, as it is not compatible with newer versions of gcc otherwise.
#include "string.h"
#include "cstdlib"

follow the other instructions as given in the INSTALL file, then for configuring -

write following command after changing the header file in objdir 

$../configure CPPFLAGS=-fpermissive
$make 
$make debug
$make install


PS. this solved my problems............i had tried a LOT of other things and nothing else was working!!

---

