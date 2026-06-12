---
title: "Installing Phun"
date: 2010-10-21
forum: General Help
---

### Post by MikeSpearman on 2010-10-21
Trying to install a program called Phun. There is a linux version available and i downloaded it but when i try to run it through the terminal it gives me the error message```
error while loading shared libraries: libboost_filesystem-mt.so: cannot
open shared object file: No such file or directory
```
I have a file named libboost_fileststem.so which is what came with the program but i dont know where to find libboost_filesystem-mt.so. Anyone else having this problem or know how to fix it?

---

### Post by rattamayhorka on 2010-10-21
install it with wine... works perfectly

sudo apt-get install wine
wine ~/Downloads/Phun*.exe

---

### Post by tgm4883 on 2010-10-21
> **rattamayhorka said:**
> install it with wine... works perfectly

sudo apt-get install wine
wine ~/Downloads/Phun*.exe

Thats just wrong on so many levels.

To the OP, did you download the tar.gz from the Phun website or did you download a Deb from playdeb?

---

### Post by rattamayhorka on 2010-10-22
> **tgm4883 said:**
> Thats just wrong on so many levels.

To the OP, did you download the tar.gz from the Phun website or did you download a Deb from playdeb?
can you explainme whats wrong with that? cause i install Phun with exactly these commands or is the fact i used a windows binary?

---

### Post by tgm4883 on 2010-10-23
> **rattamayhorka said:**
> can you explainme whats wrong with that? cause i install Phun with exactly these commands or is the fact i used a windows binary?

Why install the extra overhead of Wine and use a non-native binary when there is a native binary available?

---

