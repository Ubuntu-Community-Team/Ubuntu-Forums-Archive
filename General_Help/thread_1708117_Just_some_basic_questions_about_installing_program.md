---
title: "Just some basic questions about installing programs."
date: 2011-03-16
forum: General Help
---

### Post by Xeneth on 2011-03-16
I have been getting into installing things from source, and have screwed something up so I'm going to reinstall the OS from scratch.  (I have been playing with it and want to clear out all the config files left by old programs and other programs I put on and just forgot about.)

Well this brought up a questions I am asking now. 

1. I tried installing Wireshark from code because the version in the software center is out of date, as well as some games that are not in the Software Center, but how do I keep track of what has installed from source, and is there "uninstall" commands for those?

Is there a way to request the software center to update?  The Center only has 1.2 I think, and it does not have "monitoring Mode" that I need for wireless.

---

### Post by marin123 on 2011-03-16
i suggest you add each program's repository manually.
that way you can get newest versions without compiling yourself and you will be getting updates normally.

you have wireshark ppa here:
[https://launchpad.net/~dreibh/+related-software](https://launchpad.net/~dreibh/+related-software)

---

### Post by Xeneth on 2011-03-16
Cool, This helps with this particular software, but looking for a way to uninstall and keep track of software compiled myself.

---

### Post by NumPy on 2011-03-16
> **Xeneth said:**
> Cool, This helps with this particular software, but looking for a way to uninstall and keep track of software compiled myself.

It really depends on what application you install. For instance (not saying you have just an example) if you download an application that you have to use "make, make install" to build and install; most will come with an "uninstall". But this will not be tracked by the package manager (or technically the apt system). 
This is also dependent on *you* keeping track of what you install and build manually. 
This is why its best to use the package manager if you are worried that you will install so many things you may break the system, or just drown in toying with things. 'MOST' widely used applications out there have ppa's or debs built for them. Look for those and you should be safe.

---

### Post by Xeneth on 2011-03-19
i believe I have this covered now, though I am having a couple minor problems I need to fix before cloning my drive for backup.  Thanks.

---

### Post by jerome1232 on 2011-03-19
There is also checkinstall, [http://www.asic-linux.com.mx/~izto/checkinstall/](http://www.asic-linux.com.mx/~izto/checkinstall/)


My understanding is it is not perfect but it will create a rpm/deb package and install it with rpm/dpkg which makes it much easier to track your software.

---

