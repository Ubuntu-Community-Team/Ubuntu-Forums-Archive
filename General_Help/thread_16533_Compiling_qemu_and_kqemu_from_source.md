---
title: "Compiling qemu and kqemu from source"
date: 2005-02-22
forum: General Help
---

### Post by arnoct on 2005-02-22
Hey,

I'm having a bit of a problem getting qemu and kqemu compiled. On the website, it says that I just need to have kqemu in the qemu directory, which I do, and it'll compile when I compile qemu. However this is not working. I'm using one of the latest CVS sources of qemu, but kqemu just doesn't like to be installed (modprobing it after install does nothing.) I followed the instructions on the site; right now I'm just lost as to what I need to do.

---

### Post by quattro on 2005-02-22
well, after running modprobe kqemu, it will just load the module so the kernel aware of it. 

Did you make the kqemu device? When you launch qemu, did it complain that it could not load kqemu?

---

### Post by arnoct on 2005-02-22
I was under the impression that it added the device after compilation; my friend running a gentoo install had no problems getting it set up. How do I go about setting up the device?

[edit] OK, I have it, kinda. /dev/kqemu is present, however when I run "make" I get the following error:

make -C  SUBDIRS=`pwd` modules
make: *** SUBDIRS=/home/aaron/qemu-snapshot-2005-02-19_23/kqemu: No such file or directory.  Stop.
make: *** [kqemu.o] Error 2

Running "make install" and then "install" afterwards creates the /dev/kqemu just fine, however does not install the module. Also, I know that qemu has not compiled with kqemu support as the option -no-kqemu does not work (which would work if kqemu support was present.)

Did I screw something up? I extracted the qemu directory to ~ and kqemu into the directory that the tar made. Did I structure it wrong or something? I'm about at my wit's end now :\

---

### Post by TJ_The_Dude on 2005-03-11
Can anyone help with this? I'm having the same problem.

---

### Post by TJ_The_Dude on 2005-03-16
Just in case it helps anyone: I solved my problem by installing the "linux-headers" package corresponding to my kernel, and libsdl

./configure as root or else it might not detect sdl

---

