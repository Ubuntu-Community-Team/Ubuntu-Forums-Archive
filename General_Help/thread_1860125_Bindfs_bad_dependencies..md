---
title: "Bindfs bad dependencies."
date: 2011-10-14
forum: General Help
---

### Post by Derek Karpinski on 2011-10-14
bindfs will not install in 11.10. Some dependent packages are missing or bad.
 
[http://packages.ubuntu.com/oneiric/bindfs](http://packages.ubuntu.com/oneiric/bindfs)
 
I use bindfs to mount a public directory that is shared by several users.
 
I need this functionality........can someone suggest an alternative?

---

### Post by WorMzy on 2011-10-14
Looks like a typo. It should depend on fuse-utils, not "fuse"

Have you filed a bug?

[https://bugs.launchpad.net/ubuntu/+source/bindfs/+filebug](https://bugs.launchpad.net/ubuntu/+source/bindfs/+filebug)

---

### Post by Derek Karpinski on 2011-10-14
One has been filed, and somone repackaged it with a fuse-util dependency instead of fuse. So you're right.
 
Just for my own knowledge, does the developer determine dependencies when he packages it into a .deb file?  Or do the dependencies get called out in the source code?

---

### Post by WorMzy on 2011-10-14
Both.

The source code will tell the compiler to drag in various header files (or whatnot) during the compilation process, but it's up to the packager to make sure that s/he "connects the dots" as it were and lists the packages that the end user will need to have installed for the application to work (as well as any optional dependencies that add any extra functionality).

---

### Post by Derek Karpinski on 2011-10-14
Thanks for explaining WorMzy.

---

