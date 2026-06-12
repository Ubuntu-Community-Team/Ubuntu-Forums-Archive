---
title: "How do I remove a dependency from a package?"
date: 2010-07-29
forum: General Help
---

### Post by lykwydchykyn on 2010-07-29
I have an annoying problem.

I downloaded printer drivers for my canon printer in .deb format (they are not in the repositories, probably proprietary).  The files are 
```

cnijfilter-common
cnijfilter-mp610series

```

cnijfilter-common has a hard dependency on libcupsys2, but when I try to install it it won't install because libcupsys2 is a virtual package.

I can use "dpkg --force-all -i" to install the package, but every time I go to update or install anything else, the package manager has them marked broken and wants to remove them.  The drivers work just fine when forced, because the needed libraries are installed, they just install under a different package name nowadays.

Is there a way I can edit these .deb files and remove the dependency?

---

### Post by marshmallow1304 on 2010-07-29
Here's a script to do it quite easily.
[http://ubuntuforums.org/showpost.php?p=5585977&postcount=4](http://ubuntuforums.org/showpost.php?p=5585977&postcount=4)

---

### Post by lykwydchykyn on 2010-07-29
> **marshmallow1304 said:**
> Here's a script to do it quite easily.
[http://ubuntuforums.org/showpost.php?p=5585977&postcount=4](http://ubuntuforums.org/showpost.php?p=5585977&postcount=4)

This did the trick.  Thanks!

---

### Post by sisco311 on 2010-07-29
You have to install libcups2. 

> [size=3]**7.8 What is a Virtual Package?**[/size]


A virtual package is a generic name that applies to any one of a group of packages, all of which provide similar basic functionality. For example, both the tin and trn programs are news readers, and should therefore satisfy any dependency of a program that required a news reader on a system, in order to work or to be useful. They are therefore both said to provide the "virtual package" called news-reader. 

Similarly, smail and sendmail both provide the functionality of a mail transport agent. They are therefore said to provide the virtual package, "mail transport agent". If either one is installed, then any program depending on the installation of a mail-transport-agent will be satisfied by the existence of this virtual package.
[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)

---

### Post by lykwydchykyn on 2010-07-29
> **sisco311 said:**
> You have to install libcups2. 


[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)

It *was* installed (and still is).  Libcupsys2 (the virtual package) also is installed.  I don't know why the error, other than that it had a version requirement in the dependency, and virtual packages don't have versions. (just a theory).

---

