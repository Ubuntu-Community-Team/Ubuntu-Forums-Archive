---
title: "Glib problem"
date: 2006-02-18
forum: General Help
---

### Post by Solver on 2006-02-18
Just like (probably) many other people here, curiosity got the better of me yesterday and I decided to check out what Ubuntu is all about. Installed it, mostly worked immediately, although I had to configure it a little bit, and my first impression is overall very favorable. Now, on to the issue.

I downloaded a program tarball from the Net, tried to ./configure it, was surprised that the default Ubtuntu installation didn't even give me a C++ compiler. I think having a compiler in the default setup would be a good idea, but that's a different topic. I installed g++ and a few other packages, and now the following error output I get on ./configure:

```
checking for glib-2.0... checking for glib-config... no
checking for glib12-config... no
checking for glib-config... no
checking for GLIB - version >= 1.2.6... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: Test for glib failed.

```

I do, however, have the libglib package installed, according to Synaptic. I assume, though, glib isn't libglib. And, there's no file named glib-config on my computer. I searched the Web but didn't exactly get any idea of where it should be... so what should I do now? I suspect that there is some package missing, but there's no package showing in Synaptic named simply glib.

Thanks!

---

### Post by o_fortuna on 2006-02-18
[QUOTE=Solver]Just like (probably) many other people here, curiosity got the better of me yesterday and I decided to check out what Ubuntu is all about. Installed it, mostly worked immediately, although I had to configure it a little bit, and my first impression is overall very favorable. Now, on to the issue.

I downloaded a program tarball from the Net, tried to ./configure it, was surprised that the default Ubtuntu installation didn't even give me a C++ compiler. I think having a compiler in the default setup would be a good idea, but that's a different topic. I installed g++ and a few other packages, and now the following error output I get on ./configure:

```
checking for glib-2.0... checking for glib-config... no
checking for glib12-config... no
checking for glib-config... no
checking for GLIB - version >= 1.2.6... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: Test for glib failed.

```

I do, however, have the libglib package installed, according to Synaptic. I assume, though, glib isn't libglib. And, there's no file named glib-config on my computer. I searched the Web but didn't exactly get any idea of where it should be... so what should I do now? I suspect that there is some package missing, but there's no package showing in Synaptic named simply glib.

Thanks![/QUOTE]
Well, the first thing I always do when I install Ubuntu is get the build-essential package (sudo apt-get install build-essential), which installs all the compilers and stuff that you need. Also, if you want to compile and it says you don't have glib, try installing libglib1.2-dev and libglib2.0-dev, which will include the files you need.

---

### Post by Solver on 2006-02-18
Already had build-essential installed, but installing libglib2.0-dev fixed the problem, thanks!

Now going to see if the rest works :).

---

### Post by slacker82 on 2006-04-28
Thanks ;)
This solution works to install libglib2.0-* packages :-D

---

