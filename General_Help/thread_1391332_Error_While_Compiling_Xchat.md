---
title: "Error While Compiling Xchat"
date: 2010-01-26
forum: General Help
---

### Post by coldfusion1313 on 2010-01-26
I am compiling Xchat and when I was 'make install' I get this error and yes I am root.

```
make[2]: *** [fe-gtk.o] Error 1
make[2]: Leaving directory `/home/mark/build/xchat-2.8.6/src/fe-gtk'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/mark/build/xchat-2.8.6/src'
make: *** [install-recursive] Error 1

```I am pretty new with compiling, so all help will be accepted. 
Thanks Mark

---

### Post by Finalfantasykid on 2010-01-26
usually for the 'make install' part of compiling, you will have to do this instead...

```
 sudo make install
```

Oh nm, you are already root :P

---

### Post by Bradj47 on 2010-01-26
Unless you have to compile it, you should be able to type```
$ sudo apt-get install xchat
``` into the the terminal and should install without problems. Or you could [download the deb package]("http://packages.ubuntu.com/jaunty/xchat"). If you must compile it, this might help: [http://ubuntuforums.org/showthread.php?t=29471](http://ubuntuforums.org/showthread.php?t=29471)

---

### Post by coldfusion1313 on 2010-01-26
i did just download it but thanks for the help

---

