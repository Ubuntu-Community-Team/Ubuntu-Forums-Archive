---
title: "Need help installing bmpanel2"
date: 2011-03-12
forum: General Help
---

### Post by Lancro on 2011-03-12
I wanted to try bmpanel2, so I downloaded it, and I followed the "simple" instructions...

cmake . && make && make install

Some errors appeared, packages not found, but I solved it installing them throught synaptic, when I solved the packages issue, now the error is at follows...


In file included from /home/neira/Descargas/bmpanel2-2.1pre1/gui.h:7,
                 from /home/neira/Descargas/bmpanel2-2.1pre1/bmpanel.c:5:
/home/neira/Descargas/bmpanel2-2.1pre1/xutil.h:7: fatal error: X11/extensions/shape.h: No existe el fichero o el directorio

"No existe el fichero o el directorio" means, file not found, so I dont know what to do next, some help will be apreciated.

Thanks.

---

### Post by Krytarik on 2011-03-13
Hi, why don't you just install it from this PPA?:
[https://launchpad.net/~alex-p/+archive/notesalexp](https://launchpad.net/~alex-p/+archive/notesalexp)

---

### Post by Lancro on 2011-03-13
Thanks, the ppa works, I didnt knew it.

---

### Post by Krytarik on 2011-03-13
There is at least one PPA for almost every app not included in the official repos. I found this one by simply googling for it after reading your post.

PS: Please mark your thread as "solved" then, via "Thread Tools".

---

