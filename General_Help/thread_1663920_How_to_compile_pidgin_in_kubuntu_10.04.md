---
title: "How to compile pidgin in kubuntu 10.04"
date: 2011-01-10
forum: General Help
---

### Post by Seepgood on 2011-01-10
Hi, I am running kubuntu 10.04 and I would like to compile the newest version of pidgin (2.7.7) since its not yet included in the repositories. Except the security risks, will I have any conflicts with the installed version of pidgin (2.6.6)? Do I have to uninstall it first? Thanks.

---

### Post by taseedorf on 2011-01-10
Yep, you should uninstall it first.  If you're compiling it from source, open up a terminal in the directory you downloaded it to...run make, make install, etc... to compile it.

or find a .deb package and just install it much more simple.

---

### Post by ankspo71 on 2011-01-12
Hi,
I would recommend uninstalling the previous version first when compiling a newer version of anything too.

I just found this method of installing the newest version pidgin in Ubuntu which doesn't require compiling:
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

The link contains info on how to add Pidgin's PPA repository, so that you will be able to install the latest version of Pidgin and be able to get future updates for it. Since the package is specifically made for *Ubuntu (unlike a source package), removal of the previous version of Pidgin probably won't matter. 

Hope this helps

---

