---
title: "checking for dependencies"
date: 2009-08-29
forum: General Help
---

### Post by rcayea on 2009-08-29
How do I check for missing dependencies? To be specific, in the example below is a missing dependency anything that has the "...no" after it or the message that says "configure error"?

```
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for setlocale in -lxpg4... no
checking for ID3Tag_Link in -lid3... no
configure: error: libid3 not found
```


thanks,
Randy

---

### Post by TeoBigusGeekus on 2009-08-29
Open Synaptic, search for libid3, install it and try again.

---

