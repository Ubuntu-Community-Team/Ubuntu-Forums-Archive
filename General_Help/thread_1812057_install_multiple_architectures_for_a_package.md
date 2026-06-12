---
title: "install multiple architectures for a package?"
date: 2011-07-25
forum: General Help
---

### Post by discoross on 2011-07-25
Hi all,

I'm not sure if this is the right place, but it didn't seem to fit anywhere else. I have one specific development package in mind now, but the problem seems general.

I'm running 64bit, and I have the package liblapack-dev already installed. In order to compile some programs for a 32bit system, I installed a multilib version of g++, but I need the corresponding liblapack-dev, and all its dependencies.
[This link]("http://packages.ubuntu.com/lucid/liblapack-dev") has the 32bit package, and I started manually extracting files from the package I needed into /usr/lib32 and imitating the symbolic links that I saw in /usr/lib for my x64 version. But with all the dependencies of this library, this turned out to be tedious.

Is there a way to install a 32-bit package (and all its dependencies) on a x64 machine with a package manager?

---

### Post by CatKiller on 2011-07-25
> **discoross said:**
> Is there a way to install a 32-bit package (and all its dependencies) on a x64 machine with a package manager?

Not quite a package manager, but a script. [Getlibs]("http://explore-ubuntu.blogspot.com/2010/04/getlibs.html") does exactly that.

---

