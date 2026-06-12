---
title: "Compiling fgrun"
date: 2009-09-02
forum: General Help
---

### Post by Phantom Hoover on 2009-09-02
[LEFT]I am attempting to compile fgrun from source, but when I run the configure script it prints the following:

checking for boostlib >= 1.34.0... configure: error: We could not detect the boost libraries (version 1.34 or higher). If you have a staged boost library (still not installed) please specify $BOOST_ROOT in your environment and do not give a PATH to --with-boost option.  If you are sure you have boost installed, then check your version number looking in <boost/version.hpp>. See [http://randspringer.de/boost](http://randspringer.de/boost) for more documentation.

and refuses to go any further. It is not immediately obvious which package to install.
__[/LEFT]

---

### Post by Bachstelze on 2009-09-02
```
sudo apt-get install libboost-dev
```

---

### Post by Phantom Hoover on 2009-09-03
I've given up on compiling it; where can I find a binary for 9.04?

---

### Post by t0p on 2009-09-03
> **Phantom Hoover said:**
> I've given up on compiling it; where can I find a binary for 9.04?

I don't know.  Google might be able to help.

If you decide to try compiling (this or anything else) again, first of all check [this guide]("https://help.ubuntu.com/community/CompilingEasyHowTo").  It has a lot of info on how to do compiling correctly, including how to locate the dependencies that the compile command says you need.  It makes compiling a lot easier.

---

