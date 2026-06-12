---
title: "Ubuntu slow starting"
date: 2010-03-18
forum: General Help
---

### Post by gandalf458 on 2010-03-18
I've had Ubuntu on my laptop for almost 2 years and have upgraded it each time. It is now getting quite slow in starting up these days - comparative to when the PC was new, it's still faster than Windows.

I just wondered if there is some "housekeeping" I should be doing?

---

### Post by N92 on 2010-03-18
you can try going to your toolbar  System - Preferences - Startup Applications and remove programs that do not need to be started at startup.   But about every 2 years or so it is a good idea to backup your computer and reinstall Ubuntu to get rid of unused programs that you probably don't even use.  That will also make it boot faster.

---

### Post by _h_ on 2010-03-18
You can install [Bleachbit]("http://bleachbit.sourceforge.net/"), which will clean up your system of old debris laying around, which may or may not help you out.

Also suggest getting preload, which is an adaptive readahead daemon and works quite nicely:

```
sudo apt-get preload
```

---

### Post by N92 on 2010-03-18
[QUOTE=_h_;8989555]You can install [Bleachbit]("http://bleachbit.sourceforge.net/"), which will clean up your system of old debris laying around, which may or may not help you out.

Be careful when using any clean up software as you can accidentally remove important packages!

---

### Post by linuxman94 on 2010-03-18
> **_h_ said:**
> You can install [Bleachbit]("http://bleachbit.sourceforge.net/"), which will clean up your system of old debris laying around, which may or may not help you out.

Also suggest getting preload, which is an adaptive readahead daemon and works quite nicely:

```
sudo apt-get preload
```

The correct code is:

```
sudo apt-get install preload
```

---

### Post by ManyuX95 on 2010-03-18
I think the best solution is to format the drive as N92 said, also maybe it is the type of extention your Hard Drive has(EXT2, EXT3, blabla). Hope it helps :)

---

### Post by gandalf458 on 2010-03-19
Thanks guys. I'll look at these solutions...

---

