---
title: "Installing Fedora/SUSE application under Ubuntu"
date: 2006-05-24
forum: General Help
---

### Post by arthur on 2006-05-24
Sadly enough, my ISP ships a **bin** executable file for the above. I take for granted it would not install under Ubuntu.
Any workaround?

---

### Post by KLineD on 2006-05-24
Well, try executing it and see what error it gives you.

Maybe  you have to make it executable so:
```

chmod +x file.bin
./file.bin

```
The first line makes file.bin executable by the OS, the second one executes it.

---

### Post by arthur on 2006-05-24
Thanks. Tried what you said.

[B]ERROR MESSAGE (translated):

An error occurred.
Error running /usr/bin/chcon -R system_u:object_r:lib_t /opt/escritorio-generic-3.3/GENERIC/escritorio._scramble.so : /bin/sh: /usr/bin/chcon: No such file or directory
The installation programme will stop now[/B]

---

### Post by richbarna on 2006-05-24
[QUOTE=arthur]Sadly enough, my ISP ships a **bin** executable file for the above. I take for granted it would not install under Ubuntu.
Any workaround?[/QUOTE]

What is the file ?
Maybe there is an Ubuntu alternative.

---

