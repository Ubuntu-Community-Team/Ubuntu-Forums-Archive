---
title: "Downgrading gcc on 9.10"
date: 2010-02-10
forum: General Help
---

### Post by harisund on 2010-02-10
Hey 

I need to work on CUDA, nVidia's API for GPU development. The gcc version it requires is one step below what 9.10 provides, but it works on 9.04 

I understand it ultimately comes down to installing the appropriate packages, changing symlinks of gcc and to point to the correct version. 

So, is there an "official Ubuntu way" to do it? As in, is there some transitional or script that does it all? 

(The reason I am asking this is, generally whenever I do something like this on my own, it ends up breaking something somewhere, but if there's an official way to do it, it plays well with the rest of the system.)

---

### Post by gmargo on 2010-02-11
According to the package search page: _[http://packages.ubuntu.com/search?keywords=gcc&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=gcc&searchon=names&suite=karmic&section=all)_ there are several gcc packages available for karmic, all of which can be installed in parallel.  Will one of these do?

gcc-4.1 (version 4.1.2)
gcc-4.2 (version 4.2.4)
gcc-4.3 (version 4.3.4)
gcc-4.4 (version 4.4.1) (default)

---

### Post by harisund on 2010-02-12
Well, right now I have installed gcc-4.3 and g++4.3 and then changed the symlinks in /usr/bin/gcc and /usr/bin/g++ to now point to the above 2 packages instead of gcc-4.4 and g++-4.4

CUDA works.

Obviously, I am afraid of making a change in /usr/bin myself like that. Doing it might break something else somewhere. Isn't there like a update-alternative to do that? etc etc .. 

Besides, messing with the C compiler is always bad. I have seen softwares that require the system C compiler to be the same one that is used to compile the kernel and stuff like that.

---

### Post by gmargo on 2010-02-12
gcc is not installed in the alternatives system by default (not listed in /etc/alternatives, and no list from "update-alternatives --list gcc"), however "cc" is, and points to "gcc" so you could modify that.

Try this first:
```

export CC=gcc-4.3
export CXX=g++-4.3
make -e

```You could also create directories of symlinks to gcc-* and modify your $PATH to hit the appropriate one first.

---

