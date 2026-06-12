---
title: "Hydra gtk error"
date: 2009-10-01
forum: General Help
---

### Post by redheart419 on 2009-10-01
Hi,
I was trying to install xhydra from source but it did not compile, so I tried to install it through Hydra.sh from [http://www.hacktoolrepository.com/tool/37/Hydra](http://www.hacktoolrepository.com/tool/37/Hydra)
Well, the gtk did appear but when I tried to use it, it gave me an error massage like this> ** (xhydra:12430): WARNING **: callbacks.c 529: popen_rw_unbuffered: execv() returned

** (xhydra:12430): WARNING **: /usr/local/bin/hydra

** (xhydra:12430): WARNING **: 127.0.0.1

** (xhydra:12430): WARNING **: cisco

** (xhydra:12430): WARNING **: -l

** (xhydra:12430): WARNING **: yourname

** (xhydra:12430): WARNING **: -p

** (xhydra:12430): WARNING **: yourpass

** (xhydra:12430): WARNING **: -t

** (xhydra:12430): WARNING **: 36

** ERROR **: file callbacks.c: line 544 (popen_re_unbuffered): should not be reached

and what is worst, my hydra shell is also not working
I tried removing and reinstalling it but to no avail
If there is any way I can reform my hydra shell plz help

Thnx in advance

---

### Post by arfego on 2010-07-06
First.. Make clean after that
./configure  -- Next
joe-vim-pico *(here use u favorite editor)* **Makefile**
delete **-DLIBPOSTGRES** and **-lpq**.. (look at the first lines).
and now just make... sudo make install and that-s all folks
Hope useful
Sayounara ;)

---

