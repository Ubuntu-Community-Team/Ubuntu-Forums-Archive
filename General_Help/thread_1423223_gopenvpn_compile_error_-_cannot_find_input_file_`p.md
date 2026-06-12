---
title: "gopenvpn compile error - cannot find input file: `po/Makefile.in.in'"
date: 2010-03-06
forum: General Help
---

### Post by conmat on 2010-03-06
Ubuntu 9.10 64-bit
Lenovo T400

I'm trying to install gopenvpn from source.
[http://gopenvpn.sourceforge.net/](http://gopenvpn.sourceforge.net/)

I'm pretty sure I have all the necessary libraries installed.

./configure ends with:

.
.
.
configure: creating ./config.status
config.status: creating Makefile
config.status: creating pixmaps/Makefile
config.status: creating src/Makefile
config.status: error: cannot find input file: `po/Makefile.in.in'

Any suggestions appreciated.

---

### Post by idumych on 2010-11-20
I'm having the exact same problem, any solutions yet?

---

### Post by conmat on 2010-12-06
Sorry, I gave up.

---

### Post by jascc on 2011-02-01
I figured it out! You have to run intltoolize before ./configure. So the sequence of commands goes like this:
./autogen.sh
intltoolize
./configure
make
sudo make install

If you don't have intltoolize you probably have to install the intltool package. I'm on 10.10 btw.

---

### Post by drkitty on 2011-04-05
Thank you for this!  I was stuck too.

---

### Post by Azazel on 2011-11-10
thanks jascc! this worked for me.

---

### Post by digc16 on 2012-02-06
Has anyone encountered an error after compiling gopenvpn.

gopenvpn could not find some required resources: file gopenvpn.glade was not found.

---

