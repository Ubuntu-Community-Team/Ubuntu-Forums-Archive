---
title: "How to compile and install via terminal?"
date: 2011-03-04
forum: General Help
---

### Post by cblnchat on 2011-03-04
Im still really new to compiling and installing via terminal.  Ive only sucessfully done it to one thing, Xmoto 0.5.5.  And im gonna have to do it again but i think i got it.  But my question is, is there a general way to compile and install with
```

make

```
and
```

sudo make install

```
or is there more specific ways to do it?

Thanks

---

### Post by Krytarik on 2011-03-05
Generally, using "checkinstall" instead of just "install" is a good idea, I also just recently learned about it after doing no compiling for quite a while:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

This way a deb package will be created and installed, and you can handle those with any package manager, meaning you can safely remove it if needed.

---

### Post by jerome1232 on 2011-03-05
Read the documentation that comes with the software you are attempting to install. The developer will usually document any libraries you need to get the program compiled, and they will usually give you instructions on how to do the actual compile.

Always, read the README file that comes with the code, browse the developers site for help documentation there, it's usually going to be your best source of help since alot of things will be software specific.

---

