---
title: "Make install Problem."
date: 2010-04-24
forum: General Help
---

### Post by KingOfDeath on 2010-04-24
When i install a tar.gz File and do the command thingy This shows To EM When i do:Make install,something like this shows to me.i translated it so it may not the same.
```
make: *** No rule to make target `install '. stop!.
```
How To Fix This ?

---

### Post by blubaustin on 2010-04-24
make sure to read the read me. Usually the error only comes up if you didn't do the following
./configure

make

then make install

---

### Post by VCoolio on 2010-04-24
You may even need ./autogen.sh first to generate the files needed for compiling. Also for installing compiled stuff you may want to use [checkinstall]("https://help.ubuntu.com/community/CheckInstall"); it creates a deb and installs that, so your package manager is aware of it and you can also remove it easily later.

---

