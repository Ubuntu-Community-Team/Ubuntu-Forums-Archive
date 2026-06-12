---
title: "Getting libg2c library"
date: 2012-04-05
forum: General Help
---

### Post by Lyuokdea on 2012-04-05
Hi All,

I have a package that needs the library libg2c.so.0 which used to exist on my old version of Ubuntu, but seems to have been removed in the upgrade -- it seems to be a deprecated fortran library - any easy way to install it?

Thanks,

~Lyuokdea

---

### Post by hughr2005 on 2012-04-05
I did a bit of looking, and I *think* this may help. [http://lists.freebsd.org/pipermail/freebsd-emulation/2006-July/002307.html](http://lists.freebsd.org/pipermail/freebsd-emulation/2006-July/002307.html)

You could try ```
sudo apt-get install gcc-g77
```

---

### Post by Lyuokdea on 2012-04-05
Just figured it out -- for anybody's future reference, you need to install:

sudo apt-get install libstdc++5

Thanks for the quick reply, it set me on the right track!

~Lyuokdea

---

### Post by ohmouz on 2012-04-23
Hi,

you have given a reference  libstdc++5 to get libg2c.so.0.

How can you get libg2c from libstdc++5 on ubuntu 11.10? can you be more specific. 

Thanks,
O.

---

