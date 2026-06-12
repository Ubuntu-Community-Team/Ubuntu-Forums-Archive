---
title: "&quot;zip error: Nothing to do!&quot; when compiling"
date: 2010-03-31
forum: General Help
---

### Post by X_Splinter on 2010-03-31
Hi there I am compiling Warzone 2100 2.2.4 and get the fowling error when performing "make"

```
make[4]: Entering directory `/home/x_splinter/Área de Trabalho/warzone2100-2.2.4/data/mods/multiplay'
(cd ./original && zip -ru0 /home/x_splinter/Área de Trabalho/warzone2100-2.2.4/data/mods/multiplay/original.wz doc images messages stats wrf -x '*svn*' || [ $? -eq 12 ] && true) # zip returns 12 on "nothing to do"
	zip warning: name not matched: de
	zip warning: name not matched: Trabalho/warzone2100-2.2.4/data/mods/multiplay/original.wz
zip -T original.wz

zip error: Nothing to do! (original.wz)
make[4]: *** [original.wz] Error 12
make[4]: Leaving directory `/home/x_splinter/Área de Trabalho/warzone2100-2.2.4/data/mods/multiplay'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/x_splinter/Área de Trabalho/warzone2100-2.2.4/data/mods'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/x_splinter/Área de Trabalho/warzone2100-2.2.4/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/x_splinter/Área de Trabalho/warzone2100-2.2.4'
make: *** [all] Error 2

```

What the hell is it? How can fix it?

Thanks

---

### Post by gmargo on 2010-03-31
My bet is on an error in the makefile, such that it won't handle directories with a space in it.  Try renaming your directory to eliminate the spaces.

---

### Post by X_Splinter on 2010-03-31
> **gmargo said:**
> My bet is on an error in the makefile, such that it won't handle directories with a space in it.  Try renaming your directory to eliminate the spaces.

Nope, still got the exactly same error. Any ideas?

---

### Post by X_Splinter on 2010-03-31
Got it, I forgot to type "./autogen.sh" before the config and make

---

