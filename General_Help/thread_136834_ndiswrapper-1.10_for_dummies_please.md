---
title: "ndiswrapper-1.10 for dummies please"
date: 2006-02-26
forum: General Help
---

### Post by exiled.canuck on 2006-02-26
Hello, I've been trying to install ndiswrapper for a couple days now and am not getting anywhere.  I had it up and running on my system before when I was just running Ubuntu but did something stupid and got rid of it.  Even when I had it on before I needed the help of an experienced user to figure out why it wasn't working when I followed the instructions.  Now I am experiencing the same problems and am unsure as to what to do to connect it properly.  Based on error messages I it might have something to do with kernel headers but I am new at all of this so what I think really doesn't count for much ...

when I go through instructions in install file this comes up

userx@Amalthea:~/ndiswrapper-1.10$ sudo make uninstall
Password:
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper': Is a directory
make: *** [uninstall] Error 1

and for make install

userx@Amalthea:~/ndiswrapper-1.10$ sudo make install
Password:
make -C driver install
make[1]: Entering directory `/home/userx/ndiswrapper-1.10/driver'
Can't find kernel sources in /lib/modules/2.6.12-10-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/userx/ndiswrapper-1.10/driver'
make: *** [install] Error 2
userx@Amalthea:~/ndiswrapper-1.10$

has anyone else experienced this problem? I'm sure it is a simple thing to fix but my newbieness stops me from being able to know what to do.  Thanks for any responces

---

### Post by qb4ever on 2006-02-26
Make can't find the kernel sources and neither can I for 2.6.12-10 in the repositories.

Is there a reason you are installing it from source?

ubuntu has a package for ndiswrapper:
sudo apt-get install ndiswrapper-utils

---

