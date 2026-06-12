---
title: "Compiling libs under a different directory"
date: 2010-02-21
forum: General Help
---

### Post by unix2010 on 2010-02-21
Hi,
I am fairly new to ubuntu. I have to compile some libraries under ubuntu in a directory other than the default directory and then get the shared object libs (.so) libs for building some custome kernels.

I created a directory structure as follows:
/home/username/build-target
/home/username/src-<libname> =>here are the source files for the lib. I need to compile

Now I create a directory /home/username/src-openssl and download the source code and untar it under this directory and issue ./configure --prefix=/home/username/build-target --exec-prefix=/home/username/build-target and then make and make install.
I was expecting that the shared object libraries created (.so) files should have gone under /home/username/build-target/libs, however I just see only libssl.a and libcrypto.a and not .so files under the build-target/lib directory.

For grep also I did the same thing as above however I don't see any lib directory created under build-target directory as I was expecting.

Appreciate if anyone can guide me as to where the .so files are created or is there any switch which I need to activate for the libraries to be put under user defined directory.

Thanks for help,
Unix2010

---

### Post by unix2010 on 2010-02-22
Hi all ubuntu experts,
Appreciate any help or pointers if what I am trying to do is right or I am totally going in the wrong direction.
Thanks

---

