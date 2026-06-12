---
title: "weird conky problem"
date: 2011-05-31
forum: General Help
---

### Post by nonedrinkwater on 2011-05-31
so i installed conky colors, and it only works if i throw the conky command as root to activate conky colors, otherwise it just loads the regular conky.... 

what gives???

---

### Post by ruffEdgz on 2011-05-31
Well I can only assume you are talking about the process on this website that I found:

[http://www.webupd8.org/2010/07/conky-colors-makes-your-conky-beautiful.html](http://www.webupd8.org/2010/07/conky-colors-makes-your-conky-beautiful.html)

and which command below did you do to 'make' conky-colors:
```

$ make
$ make install

or

$ sudo make
$ sudo make install

```
If you did the second one with 'sudo' in it, the owner of the conky-colors install is 'root'.

Update this post with more information when you have time.

---

### Post by nonedrinkwater on 2011-05-31
> **ruffEdgz said:**
> Well I can only assume you are talking about the process on this website that I found:

[http://www.webupd8.org/2010/07/conky-colors-makes-your-conky-beautiful.html](http://www.webupd8.org/2010/07/conky-colors-makes-your-conky-beautiful.html)

and which command below did you do to 'make' conky-colors:
```

$ make
$ make install

or

$ sudo make
$ sudo make install

```
If you did the second one with 'sudo' in it, the owner of the conky-colors install is 'root'.

Update this post with more information when you have time.


that's seems like exactly what's going on, how do i change it?

---

### Post by searchfgold6789 on 2011-05-31
```
sudo make uninstall
sudo make clean
sudo make distclean
make
sudo make install

```

---

