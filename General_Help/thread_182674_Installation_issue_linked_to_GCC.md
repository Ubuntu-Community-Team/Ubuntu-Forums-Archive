---
title: "Installation issue linked to GCC?"
date: 2006-05-26
forum: General Help
---

### Post by GabFromDenver on 2006-05-26
Hi all, 

I was trying to install 2 new programs on my brand new Ubuntu (gnomba and cheops). Both installation failed when doing the ./configure complaining that: "C compiler cannot create executables".

Here is Cheops: 
root@LMovy:/usr/local/cheops-ng-0.2.3# ./configure
loading cache ./config.cache
checking for gcc... /usr/bin/gcc
checking whether the C compiler (/usr/bin/gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
root@LMovy:/usr/local/cheops-ng-0.2.3#


Here is Gnomba: 
root@LMovy:/usr/local/gnomba-0.6.2# ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... found
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
root@LMovy:/usr/local/gnomba-0.6.2#


So I tried to see what in the world could be wrong with my gcc, and I've typed the helloWorld C program: 
gabriel@LMovy:~/test$ cat main.c
#include <stdio.h>

int main(void)
{
  printf("Hello World!\n");
  return 0;
}

When I compile it, it fails because: "main.c:1:19: error: stdio.h: No such file or directory"

Indeed, I can't find stdio.h anywhere! Is it what caused my first 2 issues? How can I cleanly solve this?

Thanks in advance :)

          Gabriel

---

### Post by ifokkema on 2006-05-26
Hi,

Have you tried:
```
sudo apt-get install build-essential
```
?

Ivo

---

### Post by praxxus on 2006-05-26
Fantastic!
Had a similar error trying to install a package  and your suggestion fixed my situation as well.
Thanks :)

---

### Post by GabFromDenver on 2006-05-30
Yep, thanks! That was my problem...

I actually read about it this week end in the "Ubuntu user guide". It's been quite useful. I'd also recommend to new Ubuntu user like me the following link:
[http://ubuntuguide.org/]("http://ubuntuguide.org/")

---

