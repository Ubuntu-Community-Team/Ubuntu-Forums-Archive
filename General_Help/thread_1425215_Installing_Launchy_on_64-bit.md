---
title: "Installing Launchy on 64-bit"
date: 2010-03-08
forum: General Help
---

### Post by souta95 on 2010-03-08
Is it possible to install Launchy on 64-bit Ubuntu?  The only deb package provided is an i386 which gave me "Error: Wrong architecture 'i386'" when I tried to install it.

Its open source, so I could compile it myself if I had instructions.

I apologise if this is a common type of question, but I am new to 64-bit, and I'm not a programmer.

---

### Post by Joh739 on 2010-03-14
Well I suppose you can take the source and compile it yourself, but I have an easier solution. You can simply override the 32bit warning by executing the *--force-architecture* in *dpkg*.

In a terminal:
```
sudo apt-get install libqt4-core libqt4-gui ia32-libs
sudo dpkg -i --force-architecture launchy_2.1.2-1_i386.deb
```

The top line is for installing the dependencies, since the *--force-architecture* won't do it for you. Afterward it should work, at least it does with me. *ia32-libs* is needed to run 32 bit software.

---

### Post by souta95 on 2010-03-16
Thank you! It worked!

---

