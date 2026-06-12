---
title: "GTK problem"
date: 2006-04-26
forum: General Help
---

### Post by Omaha on 2006-04-26
Hi,

When I try to compile my helloworld.c file with gcc i get this error : 

~/Desktop$ gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

What should i do ? I have gtk2.8.6 installed but can't find gtk+-2.0.pc

---

### Post by cskeide on 2006-04-26
$ apt-file search gtk+-2.0.pc
libgtk2.0-dev: usr/lib/pkgconfig/gtk+-2.0.pc

try installing this package:
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by Omaha on 2006-04-26
hm, it seems to be there(/usr/lib/pkgconfig). What should i do now ?

---

### Post by cskeide on 2006-04-26
hm. try this before compiling:
```
export PKG_CONFIG_PATH="/usr/lib/pkgconfig"
```

---

### Post by Omaha on 2006-04-26
still the same problem :(

---

