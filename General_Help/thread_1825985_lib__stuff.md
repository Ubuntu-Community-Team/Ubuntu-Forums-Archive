---
title: "lib***  stuff"
date: 2011-08-16
forum: General Help
---

### Post by Hexid on 2011-08-16
[SIZE=2]I just installed Netsurf,but I was confronted with "libnsbmp  is not installed".So I installed libnsbmp.


The error "libnsgif is not installed" appeared when installing libnsbmp.
The error "libpng is not installed" appearded when installing libpnf.
...:confused:

I installed all that I was asked to install.
However,when I was installing libcss,it said that "Package libparserutils was not found in the pkg-config search path.Perhaps you should add the directory containing `libparserutils.pc'
to the PKG_CONFIG_PATH environment variable".
I have already installed libparsercutils but not in the /usr/lib dir.

What should I do to continue my installation?

And anyone could tell me what are those lib**** stuff?
I installed zlib with the apt-get install  command.Can I get other lib*** stuff with the same command? [/SIZE]

---

### Post by Bachstelze on 2011-08-16
When you want to compile software that uses a library, you should install the development file for that library. Generally they are in the packages libsomething-dev. Also, before compiling something, check whether it is in the repositories.

---

### Post by Hexid on 2011-08-16
> **Hexid said:**
> [SIZE=2]

when I was installing libcss,it said that "Package libparserutils was not found in the pkg-config search path.Perhaps you should add the directory containing `libparserutils.pc'
to the PKG_CONFIG_PATH environment variable".
I have already installed libparsercutils but not in the /usr/lib dir.

  [/SIZE]


[SIZE=2]How to[/SIZE] [SIZE=2] add the directory containing `libparserutils.pc' to the PKG_CONFIG_PATH environment variable?
TIA[/SIZE]

---

