---
title: "Error during istallation"
date: 2006-01-20
forum: General Help
---

### Post by HeSh on 2006-01-20
Hello

  I'm trying to install ubuntu on my pc, but the installation crashes while setting up packages. I've checked and found out that configuration of package "gnome-applets" crashes with this message: "assertion dependtry <=4 failed".
  Now, when i try to remove package from istallation, it says that it cannot be removed because it depends ond "gnome-applets-data" and that "gnome-applets-data" depends on "gnome-applets" so i can't remove any of those.

  Does anyone know how to bypass cofiguration and installation of this package, or to fix it so it would work?

  I'm not sure if this is connected, but when i try to install gcc package it also crashes with same message. However gcc is available but the compiler itself crashes and won't compile the simplest code.

---

### Post by HeSh on 2006-01-20
Ok, i fixed the problem with packages and managed to install everything.

GCC also works for some sample code i've written.
However i'm trying to install rp-pppoe, and it still fails during configure. I get the same message : 'C compiler cannot create executables'

The config.log file says:

configure:653: checking whether the C compiler (gcc ) works
configure:669: gcc -o conftest conftest.o 1>&5
gcc: Internal error: Segmentation fault (program cc1)
(...)

configure:failed program was:
#line 664 "configure"
#include "confdefs.h"
main(){return(0);}


EDIT:
Another thing I found out. If i compile cpp files it works fine. If the files are .C the compiler crashes.

---

