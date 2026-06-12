---
title: "i cant make conky work !"
date: 2010-04-04
forum: General Help
---

### Post by energymert on 2010-04-04
Hi guyz, i installed conky but it never worked :S Im using ubuntu 9.10 , after i installed conky i typed sudo conky but it stucked at conky : single buffer frame , but there were program barely working on the background so i typed gedit ~/,conky and i tried to edit it after that now not even working on background ! and gives me that error : ```
energy@energy-console:~$ conky
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.


```how can i fix or/and how can i uninstall that program with all files and try to download again ?

---

### Post by neur0 on 2010-04-04
Do
```
sudo apt-get purge conky && sudo apt-get install conky
```
Then try running it

---

### Post by energymert on 2010-04-04
yeah it actually downloaded again but it didnt work again it gives me the same error

---

### Post by neur0 on 2010-04-04
Then its this:
[http://ubuntuforums.org/showthread.php?t=1295621](http://ubuntuforums.org/showthread.php?t=1295621)

---

