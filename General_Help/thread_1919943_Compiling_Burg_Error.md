---
title: "Compiling Burg Error"
date: 2012-02-03
forum: General Help
---

### Post by Hman242 on 2012-02-03
When trying to compile Burg, I get an error when doing the 'make' command.

What I get is:
```
  CC    efiemu_mod-efiemu_main.o
/home/hunter/.burg/efiemu/main.c: In function ‘grub_efiemu_prepare’:
/home/hunter/.burg/efiemu/main.c:288:14: error: variable ‘err’ set but not used [-Werror=unused-but-set-variable]
cc1: all warnings being treated as errors

make: *** [efiemu_mod-efiemu_main.o] Error 1

```
I'm not sure how to proceed here. I'm not skilled at doing things like this either, I'm just following the guide @ [http://code.google.com/p/burg/wiki/ManualInstall](http://code.google.com/p/burg/wiki/ManualInstall)

---

### Post by dcstar on 2012-02-04
> **Hman242 said:**
> When trying to compile Burg, I get an error when doing the 'make' command.
.........

Why compile something that is already available as a package?

---

