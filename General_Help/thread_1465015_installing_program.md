---
title: "installing program"
date: 2010-04-29
forum: General Help
---

### Post by majikhotline on 2010-04-29
hello ubuntu country,

newbie needs help on install a torsocks program, got the files from the site but need commands to install properly. the file doesnt look like a source code so i dont think i need to compile it.  the file is in a tar.gz

What is my first step

---

### Post by CharlesA on 2010-04-29
Check to make sure it isn't in the repos first.

```
apt-cache search torsocks
```

Otherwise you will probably have to untar it and install it from source, if that's what it is.

```
tar -xf file.tgz
```

---

### Post by majikhotline on 2010-04-29
i extracted the file for torsocks...the install files want me to use cvs/svn to complie. i have never complie a program before (i sound like a newbie) lol  this is what it says ```
make -f Makefile.cvs
  ./configure
  make
  make install

```

---

