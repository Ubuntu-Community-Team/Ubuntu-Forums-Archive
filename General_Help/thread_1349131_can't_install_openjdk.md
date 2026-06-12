---
title: "can't install openjdk"
date: 2009-12-07
forum: General Help
---

### Post by creatxr on 2009-12-07
ubuntu 9.10 desktop
-----------------------------
openjdk-6-jre_6b11-2ubuntu2.1_i386.deb
openjdk-6-jre
Error: Dependency is not satisfiable: openjdk-6-jre-headless (>= 6b11-2ubuntu2.1)

openjdk-6-jre-headless_6b16-1.6.1-3ubuntu1_i386.deb
openjdk-6-jre-headless
Error: Dependency is not satisfiable: openjdk-6-jre-lib (>= 6b16-1.6.1-3ubuntu1)

openjdk-6-jre-lib_6b16-1.6.1-3ubuntu1_all.deb
openjdk-6-jre-lib
Error: Dependency is not satisfiable: openjdk-6-jre-headless (>= 6b16)
-----------------------------
the problem is openjdk-6-jre-headless need openjdk-6-jre-lib, but openjdk-6-jre-lib need openjdk-6-jre-headless at the same time, so it can't be installed.

i use *.deb for installing, because i didn't find openjdk in the package manager

it 's better that it has a portable openjdk! does someone know where to download it?

---

### Post by snova on 2009-12-08
> **creatxr said:**
> the problem is openjdk-6-jre-headless need openjdk-6-jre-lib, but openjdk-6-jre-lib need openjdk-6-jre-headless at the same time, so it can't be installed.

If you've downloaded all the .deb's, pass them all to dpkg at once. Something like:

```
sudo dpkg -i openjdk-*.deb
```

> i use *.deb for installing, because i didn't find openjdk in the package manager

That is strange, openjdk is in the main repositories. Can you not install it this way?

```
sudo apt-get install openjdk-6-jdk
```

---

### Post by creatxr on 2009-12-08
thanks.
i 've changed repositories to the "main repositories".
there aren't openjdk in the "canada repositories".

---

### Post by hh3003it on 2010-12-22
> **creatxr said:**
> thanks.
i 've changed repositories to the "main repositories".
there aren't openjdk in the "canada repositories".

Hi [creatxr]("http://ubuntuforums.org/member.php?u=957043"),

Can you help me to change repositories to the "main repositories" (how to change)?.
I have meet this problem, too.

Thank you.

---

