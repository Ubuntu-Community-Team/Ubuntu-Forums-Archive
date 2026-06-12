---
title: "Cross-Compiler Help"
date: 2011-03-25
forum: General Help
---

### Post by poxusa on 2011-03-25
Hello,
I am trying to cross-compile and getting the following error  
> bash: ../binutils-2.21/configure: No such file or directoryHowever, I have unzipped the file in "cd build-binutils" directory and into "cd crossbuild directory". I do not know why it is not building the compiler. The command I am trying to enter into Terminal is ../binutils-2.21/configure --target=$TARGET --prefix=$PREFIX --disable-nls -v
Please let me know what I am doing wrong. Thank you.

---

### Post by Lateralis on 2011-03-25
The error message is pretty clear: 'configure' does not exist at the relative path '../binutils-2.21/'.

---

### Post by poxusa on 2011-03-25
> **Lateralis said:**
> The error message is pretty clear: 'configure' does not exist at the relative path '../binutils-2.21/'.
I have config in the file, but I still get same error message bash: ../binutils-2.21/config: No such file or directory

---

