---
title: "How To Install Jitterbit"
date: 2006-06-08
forum: General Help
---

### Post by Tore Van Grembergen on 2006-06-08
I don't know if this is the right place.
If not please put me in the right direction.

Does anybody know how, or already tried to install jitterbit on Dapper Drake or Breezy Badger ?

Jitterbit is an open source client and server for integration solutions.
For the moment they only have a Fedora rpm package.

Any help is much appreciated.

Kind regards

Tore

---

### Post by zolero on 2006-06-20
[QUOTE=Tore Van Grembergen]... Jitterbit is an open source client and server for integration solutions. For the moment they only have a Fedora rpm package...
[/QUOTE]
 Hi Tore.

There is a good news for u. It is possible to install any rpm package on Breezy or Dapper. :wink: 

:-\" U need to install alien, rpm, debhelper, fakeroot and binutils on your machine for manipulatin' the rpm (or tgz; tar.gz; bz2) packages. The following are the steps:

1.) First of all get the package(s) which u want to install.

2.) Then type in terminal:

              $ sudo apt-get install alien rpm debhelper fakeroot binutils

3.) Convert packages to ubuntu-packages, by typing:

              $ sudo alien ***package-name-version.rpm***

This will make a **package-name-version-2_all.deb** , or something like this in same directory, where the rpm is located.

4.) Finally install the .deb package:

               $ sudo dpkg -i **package-name-version-2_all.deb**

That's all. :lol: 

Cheers, Zolero.

---

### Post by echo4mic on 2007-03-13
I understand about converting the rpms to debs... and that's all fine....
Unfortunately, Jitterbit has an install.sh, which expects to RPM install stuff as well as configure the Jitterbit installation.

Has anyone successfully ported this install.sh to work in Ubuntu 6.10?
Or successfully installed/config'd it by hand?

thanks,
echo4mic

---

### Post by cronky on 2008-03-08
Didn't work for me but then I discovered that they only support i386 (32bit) anyway which is a bit of a pain. Would be good to get this up and running on our Ubuntu servers.

---

### Post by sarvjita on 2008-05-30
hi
i'm new to jitterbit, can any one help me to install jitterbit in ubuntu.

thanks

---

