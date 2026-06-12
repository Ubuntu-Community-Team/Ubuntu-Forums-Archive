---
title: "what to do with sh:"
date: 2010-11-06
forum: General Help
---

### Post by linein on 2010-11-06
Hello everybody.
i've got a little bit stupid question i think...
so i'm sorry, but i'm a newbie and i need help.

i'm trying to install a driver for broadcom wifi adapter.
the driver is loaded already, and i'm doing the 3rd step : 

> 3: Setup to always load at boot time.

they tell:

> Ubuntu ships a version of wl.ko, so those need to be disabled.  On my 
system the were several versions, so I searched and renamed the .ko's
like this:

# sh: for i in `find /lib /var -name wl\.ko`; do mv $i ${i}.orig; done

so, i don't know how to do it.
what is SH: and what is the meaning of that line?

tnx a lot.

---

### Post by petersohn on 2010-11-06
sh is the name of the Bourne shell program. In English, the shell program that you use when you open the terminal. To be precise, you actually use bash, which is the advanced version of sh.

I don't know why "they" use that syntax, but the following line is a simple script that renames files named wl.co inside the /lib and /var directory tree to wl.ko.orig:
```
for i in `find /lib /var -name wl\.ko`; do mv $i ${i}.orig; done 
```

---

### Post by linein on 2010-11-06
so how how can i activate the scrypt?

---

