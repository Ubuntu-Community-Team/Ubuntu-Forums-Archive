---
title: "Can't Install From Source"
date: 2010-01-16
forum: General Help
---

### Post by JordanMaster22 on 2010-01-16
Alright. I was trying to install a program from source. I cd'd to the directory then ./configure'd. It was configuring fine until this.

> checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: *** GTK+ version 2.4.0 not found!

How can I fix this?

---

### Post by Sef on 2010-01-16
Did you download build-essential?  If not then from the terminal, copy and paste these codes:

```
sudo apt-get update && sudo apt-get install build-essential
```

Those codes will get you the latest version of build-essential in the repositories.

---

