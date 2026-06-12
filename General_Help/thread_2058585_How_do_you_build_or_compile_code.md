---
title: "How do you build or compile code?"
date: 2012-09-16
forum: General Help
---

### Post by clay7 on 2012-09-16
Hello,

I'm following instructions for installing some software, but the instructions didn't include how to build the downloaded source code. From that point on, the instructions refer to a "built" version, and since I don't know how to do this, I'm stuck.

I'm assuming that the folder I have full of **.c** and **.h** files is source code? The following files (among many others) are also in the folder:

compile
configure
configure.ac
install-sh
Makefile.am

Any help in building this would be greatly appreciated.

---

### Post by Scott Harrison on 2012-09-16
Source code can have various dependencies and other unique traits that make the compilation process different. Make sure to read any "readme" files for instructions from the developer on how to build their particular code to work on your hardware.

As for the actual build process - [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by zombifier25 on 2012-09-16
Does the file has any documentation than comes with it (like an INSTALL file or README file or something)? Because I suspect the install-sh script will do everything for you. Otherwise, this is the standard procedure for compiling a program:
```
cd /path/to/folder
./configure
make
sudo make install
```
EDIT: got defeated to it

---

### Post by clay7 on 2012-09-16
Between the both of you, I was able to do this. 

I ran the autogen.sh command and that didn't do anything, so I did  ./configure and that started the process.

Thank you so much!

---

### Post by Scott Harrison on 2012-09-17
> **clay7 said:**
> Between the both of you, I was able to do this. 

I ran the autogen.sh command and that didn't do anything, so I did  ./configure and that started the process.

Thank you so much!
Not a problem. :p

---

