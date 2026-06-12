---
title: "Installing Debian Package on Ubuntu"
date: 2010-10-31
forum: General Help
---

### Post by Veered on 2010-10-31
I have been trying to install a Debian package, LumenVox (a voice recognition software suite), on Ubuntu. Here is the installation guide:
[http://www.lumenvox.com/help/speechEngine/index.htm](http://www.lumenvox.com/help/speechEngine/index.htm)

I added the repo just fine, no problems. I apt-get the necessary packages. The list that they give you has to be typed in lowercase, no uppercase. Still no big deal. Then I got a list of unresolved dependencies. I manually downloaded them and used dpkg to install them. This works for all of them except 'libc-i686'. I understand that this is already a core package in Ubuntu, and as a result cannot be installed again. However, how can I make the debian package realize this? Any help would be greatly appreciated, I am becoming quite frustrated.

---

### Post by ajgreeny on 2010-10-31
Perhaps it is the wrong version of libc-i686.  That can often happen with packages from other third party repos.

---

### Post by Veered on 2010-10-31
Oops double post

---

### Post by Veered on 2010-10-31
Is there anyway to do a parallel installation of both versions? Or to force the package to use the newer version? Whenever I try to install the Debian version of libc6 called for by the package I get:


```
dpkg: regarding libc6-i686_2.7-18lenny6_i386.deb containing libc6-i686, pre-dependency problem:
 libc6-i686 pre-depends on libc6 (= 2.7-18lenny6)
  libc6 is installed, but is version 2.12.1-0ubuntu8.
dpkg: error processing libc6-i686_2.7-18lenny6_i386.deb (--install):
 pre-dependency problem - not installing libc6-i686
Errors were encountered while processing:
 libc6-i686_2.7-18lenny6_i386.deb
```

---

### Post by Veered on 2010-11-02
Well I figured it out. All you have to do is unpackage the deb files and manually remove all of the libc6 dependencies. Repackage, install the other debian dependencies it asks for, install, and everything works perfectly!

---

