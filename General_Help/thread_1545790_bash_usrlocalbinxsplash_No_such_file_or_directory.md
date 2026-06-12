---
title: "bash: /usr/local/bin/xsplash: No such file or directory"
date: 2010-08-04
forum: General Help
---

### Post by rdnrvn on 2010-08-04
Hi,

I recently install xsplash from build. It got installed by default in /usr/local 
Now I have uninstalled it and want to go back to using xplash in /usr/bin but i get this error when I run xsplash command:

bash: /usr/local/bin/xsplash: No such file or directory

I figure its still trying to run the one in local folder. How do I changes this to run /usr/bin/xsplash like it was before I installed from the build.

Thanks.

---

### Post by luigi_mb on 2010-08-04
Try:

```

$ make clean
$ ./configure --prefix=/usr
$ make
$ sudo make install

```

/luigi

---

### Post by rdnrvn on 2010-08-04
Thanks. Im such a noob.

---

