---
title: "Add Applications errors"
date: 2006-05-15
forum: General Help
---

### Post by Chasehead on 2006-05-15
Hey I have just recently installed ubuntu on my computer as a second OS to Windows ME, and I get this error whenever I try to install applications or packages:

W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)

I am very new to ubuntu and I would appreciate any help.

---

### Post by Sef on 2006-05-15
See if it is in the sources list:

Application > Accessories > Terminal

then in the terminal type

sudo gedit /etc/apt/sources.list

then find that line in the sources and comment it out.  

Put a #at the beginning of it, if it is.

#[http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/

---

