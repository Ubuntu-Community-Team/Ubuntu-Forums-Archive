---
title: "when and how exactly upstart in ubuntu starts?"
date: 2009-11-13
forum: General Help
---

### Post by froff on 2009-11-13
hello
I can't find it in the system. I assume that normal init is called from the kernel because there is no special "init" parameter passed into kernel.
So anybody knows when and how (from what program/script) upstart starts?

---

### Post by diesch on 2009-11-13
upstart replaces the normal init:

```
$ /sbin/init --version
init (upstart 0.6.3)
Copyright (C) 2009 Canonical Ltd.

This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by froff on 2009-11-15
> **diesch said:**
> upstart replaces the normal init:

```
$ /sbin/init --version
init (upstart 0.6.3)
Copyright (C) 2009 Canonical Ltd.

This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```


O gosh! I didn't suspect :)
Thanks

---

