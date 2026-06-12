---
title: "Copy files from ldd to location"
date: 2010-01-30
forum: General Help
---

### Post by lazysloth on 2010-01-30
When I use ldd it prints the location of the depends.
Is there a way to copy the depends listed to a location in a single command or streamline it? I don't want to copy each dependence once at a time.

---

### Post by rnerwein on 2010-01-30
hi 
do you realy want to copy the libraries ?
if you get your own libraries on differnt location wich are not in the search path you can set the special path in your environment via: LD_LIBRARY_PATH=/bla/blu .... and so on
but what's about: man ld and man ldd !
ciao

---

