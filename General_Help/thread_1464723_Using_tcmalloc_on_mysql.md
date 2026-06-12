---
title: "Using tcmalloc on mysql"
date: 2010-04-28
forum: General Help
---

### Post by brian.takita on 2010-04-28
Hello, I would like to use tcmalloc from the libgoogle-perftools0 package in mysql.

The instruction at [http://www.imminentweb.com/technologies/use-tcmalloc-improve-mysql-service](http://www.imminentweb.com/technologies/use-tcmalloc-improve-mysql-service) were to add the following line to mysqld_safe:

```
LD_PRELOAD="/usr/lib/libtcmalloc.so.0"
```

However, this requires editing mysqld_safe. Ubuntu (from Debian) provides a nice way to add configuration scripts in a way that does not requiring editing packaged files.

What is the recommended way to add LD_PRELOAD without touching the mysqld_safe file. I'm a little squeamish about making a global environment variable, but I could, I suppose.

---

