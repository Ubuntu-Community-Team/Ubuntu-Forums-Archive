---
title: "How does one determine the contents of a package?"
date: 2010-07-25
forum: General Help
---

### Post by leonardevens on 2010-07-25
I am very experienced with versions of RedHat, including most recently Fedora.   Under these

rpm -ql  xxxx

will tell me the files which are part of package xxxx.

Recently, I started using ubuntu.

I haven't been able to figure out what the corresponding command(s) are for Ubuntu.

---

### Post by sisco311 on 2010-07-26
```
dpkg-query -L pkgname
```
or simply```
dpkg -L pkgname
```

Take a look at: [http://wiki.archlinux.org/index.php/Pacman_Rosetta](http://wiki.archlinux.org/index.php/Pacman_Rosetta)

---

