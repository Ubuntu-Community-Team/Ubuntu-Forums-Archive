---
title: "How to install bazaar branch"
date: 2011-10-16
forum: General Help
---

### Post by BinaryMn on 2011-10-16
Downloaded source from bzr branch lp:~gnome3-team/gnome-control-center/ubuntu

What am I supposed to do with the stuff created in ./ubuntu/debian? Nothing I do works. There is no documentation.

---

### Post by mali2297 on 2011-10-16
Perhaps you can try running 
```

cd ubuntu
dpkg-buildpackage

``` 
in a terminal. See [http://www.debian.org/doc/manuals/maint-guide/build.en.html#completebuild](http://www.debian.org/doc/manuals/maint-guide/build.en.html#completebuild).

---

