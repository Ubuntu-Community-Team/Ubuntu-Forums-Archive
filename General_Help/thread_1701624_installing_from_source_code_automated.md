---
title: "installing from source code automated"
date: 2011-03-06
forum: General Help
---

### Post by doomdude6 on 2011-03-06
hello 

i was wondering if there are any tools that automate the process of installing from source for example tar.gz or tar.bz2. i have used kludge installer but i am looking for somthing that doesn't make me install any dependencies for example i want a bash shell script it just runs the commands you normally do but faster if any has info on an program like that please let me know 
                                            thanx in advance
                                                      your friend
                                                             doomdude6

---

### Post by srs5694 on 2011-03-06
I'm not aware of such a thing, with one exception (see below). The trouble is that there's no standard for what should appear in a tarball. Some programs use a "configure" script, others use "make config", others require manual editing of the Makefile, and so on. There are also issues with dependencies -- it might be necessary to download and install support libraries or other tools.

The one exception I'm aware of is to use a source-based distribution, such as Gentoo. When you use Gentoo, instead of installing Debian packages or RPMs, you use a command called emerge, which downloads a source tarball, applies patches, compiles the package, and installs it. This works because the Gentoo developers distribute scripts for each package; emerge calls these in order to do the compiling (and everything else).

Why do you want an automatic source package installer? If you don't build source packages often, such a tool won't save you much time or effort. If you do build from source often, chances are you don't need to; you can get just about everything for Ubuntu (or other binary distributions) in precompiled form. If you're into compile-time optimizations, though, you might want to look into Gentoo. Be aware that it's not nearly as user-friendly as Ubuntu (or Fedora or OpenSUSE or various others), and managing its packages can be a hassle. You'll waste far more time than you'll save by improving the performance of your binaries by a few milliseconds. IMHO, Gentoo's advantages lie elsewhere -- it's very customizable, and you can create a version that's optimized for specific purposes if that's necessary.

---

### Post by anirudhtomer on 2011-03-06
> The  trouble is that there's no standard for what should appear in a tarball.  Some programs use a "configure" script, others use "make config",  others require manual editing of the Makefile, and so on. There are also  issues with dependencies -- it might be necessary to download and  install support libraries or other tools.

This is the right answer. The thread should be marked solved.

---

