---
title: "yet another make error"
date: 2006-02-24
forum: General Help
---

### Post by DestinyPrevails on 2006-02-24
I have read some threads and most people say that this error can be ignored but when I sill try to make install i get the same error and the thing I try to install wont be installed at all.

> 
root@b122-02:/home/c-bengh/comix-1.3.7# make
make: Warning: File `Makefile' has modification time 1e+02 s in the future
make  all-recursive
make[1]: Entering directory `/home/c-bengh/comix-1.3.7'
make[1]: Warning: File `Makefile' has modification time 1e+02 s in the future
Making all in colorscheme
make[2]: Entering directory `/home/c-bengh/comix-1.3.7/colorscheme'
make[2]: Warning: File `Makefile' has modification time 1e+02 s in the future
make[2]: Nothing to be done for `all'.
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
make[2]: Leaving directory `/home/c-bengh/comix-1.3.7/colorscheme'
Making all in style
make[2]: Entering directory `/home/c-bengh/comix-1.3.7/style'
make[2]: Warning: File `Makefile' has modification time 1e+02 s in the future
Making all in config
make[3]: Entering directory `/home/c-bengh/comix-1.3.7/style/config'
make[3]: Warning: File `Makefile' has modification time 1e+02 s in the future
make[3]: Nothing to be done for `all'.
make[3]: warning:  Clock skew detected.  Your build may be incomplete.
make[3]: Leaving directory `/home/c-bengh/comix-1.3.7/style/config'
make[3]: Entering directory `/home/c-bengh/comix-1.3.7/style'
make[3]: Warning: File `Makefile' has modification time 1e+02 s in the future
make[3]: Nothing to be done for `all-am'.
make[3]: warning:  Clock skew detected.  Your build may be incomplete.
make[3]: Leaving directory `/home/c-bengh/comix-1.3.7/style'
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
make[2]: Leaving directory `/home/c-bengh/comix-1.3.7/style'
Making all in kwin
make[2]: Entering directory `/home/c-bengh/comix-1.3.7/kwin'
make[2]: Warning: File `Makefile' has modification time 1e+02 s in the future
Making all in config
make[3]: Entering directory `/home/c-bengh/comix-1.3.7/kwin/config'
make[3]: Warning: File `Makefile' has modification time 1e+02 s in the future
make[3]: Nothing to be done for `all'.
make[3]: warning:  Clock skew detected.  Your build may be incomplete.
make[3]: Leaving directory `/home/c-bengh/comix-1.3.7/kwin/config'
make[3]: Entering directory `/home/c-bengh/comix-1.3.7/kwin'
make[3]: Warning: File `Makefile' has modification time 1e+02 s in the future
make[3]: Nothing to be done for `all-am'.
make[3]: warning:  Clock skew detected.  Your build may be incomplete.
make[3]: Leaving directory `/home/c-bengh/comix-1.3.7/kwin'
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
make[2]: Leaving directory `/home/c-bengh/comix-1.3.7/kwin'
make[2]: Entering directory `/home/c-bengh/comix-1.3.7'
make[2]: Warning: File `Makefile' has modification time 1e+02 s in the future
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
make[2]: Leaving directory `/home/c-bengh/comix-1.3.7'
make[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/home/c-bengh/comix-1.3.7'
make: warning:  Clock skew detected.  Your build may be incomplete.



My clock is at perfect time

can someone hjelp me with this??

and im a total noobie to kubuntu so plz post in words I can understand! ty!\\:D/

---

