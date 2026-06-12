---
title: "How Do I Find Out if I have a 32 or 64 Bit Ubuntu OS?"
date: 2009-10-30
forum: General Help
---

### Post by Ken Martin on 2009-10-30
I use an Asus #F8sg PC. It has Ubuntu 9.04 loaded. I want to install 9.1 but am hesitant, as I do not know if the already loaded OS is 32 or 64 bit. System Monitor information is -

Kernel Linux 2.6.28-16-generic, Gnome 2.26.1.

The HDD is dual-boot configured, with another Linux OS on the other side.

Help, guys! Thanks, Ken

---

### Post by fooman on 2009-10-30
open a terminal and type:

```
uname -a
```

post the output back here...basically,  if it ends in x86_64 GNU/Linux,  then you have 64bit installed.

---

