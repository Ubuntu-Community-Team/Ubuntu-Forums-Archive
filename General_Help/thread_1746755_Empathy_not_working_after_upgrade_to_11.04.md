---
title: "Empathy not working after upgrade to 11.04"
date: 2011-05-02
forum: General Help
---

### Post by luvshines on 2011-05-02
I upgraded from 10.10 to 11.04 and empathy has stopped working for me.

Gives following error message from terminal
```

empathy: /usr/local/lib/libtelepathy-glib.so.0: version `TELEPATHY_GLIB_0.13.11' not found (required by empathy)
```

Empathy version is 2.34.0-0ubuntu3 and libtelepathy-glib0 version is 0.14.3-1ubuntu1

Couldn't find any solution/post regarding this error message on the net

Any suggestions/help ??

---

### Post by luvshines on 2011-05-09
Worsened :)

Downloaded and installed telepathy-glib-0.13.10.tar.gz from source.
Empathy now giving following error ```

empathy: /usr/local/lib/libtelepathy-glib.so.0: version `TELEPATHY_GLIB_0.14.2' not found (required by empathy)
empathy: /usr/local/lib/libtelepathy-glib.so.0: version `TELEPATHY_GLIB_0.13.14' not found (required by empathy)
empathy: /usr/local/lib/libtelepathy-glib.so.0: version `TELEPATHY_GLIB_0.13.16' not found (required by empathy)
empathy: /usr/local/lib/libtelepathy-glib.so.0: version `TELEPATHY_GLIB_0.13.11' not found (required by empathy)

```

Any idea how to fix this ?

---

### Post by luvshines on 2011-05-09
Whoopi !! It's fixed \\:D/

Downloaded, built and installed telepathy-glib-0.14.3 from source.
Empathy started working :D

---

