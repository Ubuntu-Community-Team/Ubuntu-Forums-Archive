---
title: "Shouldn't these library versions match?"
date: 2009-08-22
forum: General Help
---

### Post by MartinEve on 2009-08-22
Hi all,

I'm having a problem with gwenview after I upgraded to KDE 4.3.

The application crashes with the error:

```

symbol lookup error: /usr/lib/libnepomuk.so.4: undefined symbol: _ZN7Soprano4NodeC1ERKNS_12LiteralValueE

```

Other sources hint that this may be a problem with libsoprano being of the incorrect version. However, I have reinstalled both libsoprano and gwenview.

I did notice this though:

ls -al /usr/lib/libnepomuk.so*
```
lrwxrwxrwx 1 root root 19 2009-08-06 17:49 /usr/lib/libnepomuk.so.4 -> libnepomuk.so.4.3.0
-rw-r--r-- 1 root root 412456 2009-07-31 13:38 /usr/lib/libnepomuk.so.4.3.0

```

whereas

ls -al /usr/lib/libsoprano.so*
```
lrwxrwxrwx 1 root root     15 2009-08-22 12:05 /usr/lib/libsoprano.so -> libsoprano.so.4
lrwxrwxrwx 1 root root     19 2009-08-22 11:55 /usr/lib/libsoprano.so.4 -> libsoprano.so.4.2.0
-rw-r--r-- 1 root root 940296 2009-07-23 05:20 /usr/lib/libsoprano.so.4.2.0

```

Shouldn't libsoprano also be 4.3.0?

Could this be causing the problem?

Thanks,

Martin

---

