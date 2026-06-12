---
title: "Cannot install .tar.gz files"
date: 2010-12-05
forum: General Help
---

### Post by Curse on 2010-12-05
Hey, I tried installing some software via ./configure, make, make install, and kept getting an error that it could not find the makefile.

I noticed at the end of ./configure it was missing a package. I found it and installed it, tried again. Next it was missing two more packages, I found one and installed it, but the other is dbus, and the only downloads I can find for dbus are .tar.gz. 

Upon downloading dbus-1.4.0, and trying the legacy version 1.2.24, I tried ./configure again.

This time I get this error: 
configure: error: Could not find expat.h, check config.log for failed attempts

So I went to the Synaptic package manager, installed expat, and tried again.

I get the same message.

I'm just going in circles at this point, please help.

---

### Post by Curse on 2010-12-05
I went into Synaptic package manager and randomly found libexpat1-dev and installed that. So far I'm now able to complete ./configure, it is running make now. If this works I'll try the original software again.

Why is this stuff not included from the start?

---

### Post by Curse on 2010-12-05
The original piece of software I'm trying to install is Gecko Mediaplayer.

I successfully installed dbus-1.4.0, but I still get the same message upon running ./configure for Gecko:

checking for DBUS... configure: error: Package requirements (dbus-1 >= 0.95 dbus-glib-1 >= 0.70) were not met:

No package 'dbus-glib-1' found

---

### Post by gandaran on 2010-12-05
> **Curse said:**
> The original piece of software I'm trying to install is Gecko Mediaplayer.

I successfully installed dbus-1.4.0, but I still get the same message upon running ./configure for Gecko:

checking for DBUS... configure: error: Package requirements (dbus-1 >= 0.95 dbus-glib-1 >= 0.70) were not met:

No package 'dbus-glib-1' found 
any reason you have to compile Gecko Mediaplayer? why don't you install from package manager.

---

### Post by lykeion on 2010-12-05
First of all, why would you go through the trouble of compiling gecko-mediaplayer when you easily could just install it with apt-get install??

If you for some reason you still would like do this, you could use the apt-get build-dep command to get all build depenencies for a package in the repositories:
```
sudo apt-get build-dep gecko-mediaplayer
```

---

### Post by oldos2er on 2010-12-05
> **Curse said:**
> The original piece of software I'm trying to install is Gecko Mediaplayer.

I successfully installed dbus-1.4.0, but I still get the same message upon running ./configure for Gecko:

checking for DBUS... configure: error: Package requirements (dbus-1 >= 0.95 dbus-glib-1 >= 0.70) were not met:

No package 'dbus-glib-1' found

I think it's looking for libdbus-glib-1-dev

---

### Post by arjunlalb on 2010-12-05
avoid the hazzle.. get a .deb package of the software you are installing, from the web and install it with software manager..

---

### Post by lykeion on 2010-12-05
> **arjunlalb said:**
> avoid the hazzle.. get a .deb package of the software you are installing, from the web and install it with software manager..
Avoid the web hazzle altogether and install it from the repositories:```
sudo apt-get install gecko-mediaplayer
```

---

### Post by Curse on 2010-12-05
> **lykeion said:**
> First of all, why would you go through the trouble of compiling gecko-mediaplayer when you easily could just install it with apt-get install??

If you for some reason you still would like do this, you could use the apt-get build-dep command to get all build depenencies for a package in the repositories:
```
sudo apt-get build-dep gecko-mediaplayer
```

Didn't know you could do that. Thank you!

Also I didn't know it was in the repositories.. I figured it wasn't because when FF tried to autoinstall it it kept failing. 

Thank you everybody!

---

