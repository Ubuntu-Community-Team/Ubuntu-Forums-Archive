---
title: "Aptitude: A next to package status"
date: 2011-04-06
forum: General Help
---

### Post by Beowolf64 on 2011-04-06
What does it mean? Couldn't find it in the manual. 

Thanks you.

---

### Post by Telengard C64 on 2011-04-06
I think that would be the (A)utomatic flag.

[quote=Aptitude User's Manual -> 2. aptitude Reference Guide -> Managing packages -> Accessing package information -> The Package List]The package list displays an “at-a-glance” synopsis of a package's state. For instance, the package webmin might have the following synopsis:
```
piAU webmin   +5837kB <none>   1.160-2
```
The four characters on the left-hand side of the synopsis show that the package is not installed (“p”), that it is going to be installed (“i”), that it was automatically chosen to be installed (“A”), and that it is untrusted (“U”). On the right-hand side of the synopsis, the current version and the most recent available version are displayed, along with an indication of how much space will be used by the upgrade.

The four status flags on the left-hand side of the screen give the basic information about a package's state. The first character is the package's current state. The second character is the action which will be taken on the package. The third character indicates whether the package was automatically installed (see the section called “Managing automatically installed packages”), and the fourth character indicates whether the package is trusted (see the section called “Understanding and managing package trust”).[/quote]

The full Aptitude documentation is available from the package [aptitude-doc-*](http://packages.ubuntu.com/search?keywords=aptitude-doc&searchon=names&suite=all&section=all)

HTH

---

