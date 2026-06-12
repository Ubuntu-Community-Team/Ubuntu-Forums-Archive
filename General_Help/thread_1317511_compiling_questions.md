---
title: "compiling questions"
date: 2009-11-06
forum: General Help
---

### Post by Eragon0605 on 2009-11-06
I have a compiling question. How do I compile a .deb package? Most guides say to cd to the directory of the source, run the "sudo ./configure" command, then run "sudo dpkg -i name_of_package.deb" I get:

dpkg: error processing bob.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
bob.deb

[COLOR=White][/COLOR]

---

### Post by 101011010010 on 2009-11-06
Hello there.
Have you tried just clicking on the .deb file?

[https://help.ubuntu.com/community/OtherWaysToInstall](https://help.ubuntu.com/community/OtherWaysToInstall)

The paragraph "Installing the standard ways", should help.
I hope this helps.

---

### Post by marshmallow1304 on 2009-11-07
Edit:  If you already have a .deb package, you don't need to compile it.  Just double click it.


> **Eragon0605 said:**
> Most guides say to cd to the directory of the source, run the "sudo ./configure" command, then run "sudo dpkg -i name_of_package.deb"

Not quite.  Generally,

cd to directory of source
```
./configure
make
sudo checkinstall
```

---

