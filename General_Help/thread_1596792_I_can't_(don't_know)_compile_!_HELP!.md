---
title: "I can't (don't know) compile ! HELP!"
date: 2010-10-14
forum: General Help
---

### Post by petrasflorin on 2010-10-14
I never compiled/installed anything from source code because everytime I tried I got all kinds of wierd errors.

For example I tried installing this:

[http://freshmeat.net/projects/libv4l](http://freshmeat.net/projects/libv4l)

I downloaded, did tar xvf (was a bz2 archive, took me some time to figure it out) , cd directory.

all ok ?

did : less install

followed instructions.


did make path (what was in the instructions)

    make install path (also in the instructions) and came up with this:

ERRORS:

root@pif-asus:/home/pif/Downloads/v4l-utils-0.8.1# make install PREFIX=/usr LIBDIR=/usr/lib32
make -C lib install
make[1]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/lib'
make -C libv4lconvert install
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/lib/libv4lconvert'
mkdir -p /usr/include
install -p -m 644 ../include/libv4lconvert.h /usr/include
mkdir -p /usr/lib32/libv4l
install -m 755 libv4lconvert.so.0 /usr/lib32
cd /usr/lib32 && \
	  ln -f -s libv4lconvert.so.0 libv4lconvert.so
install -m 755 *-decomp /usr/lib32/libv4l
mkdir -p /usr/lib32/pkgconfig
install -m 644 libv4lconvert.pc /usr/lib32/pkgconfig
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/lib/libv4lconvert'
make -C libv4l2 install
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/lib/libv4l2'
mkdir -p /usr/include
install -p -m 644 ../include/libv4l2.h /usr/include
mkdir -p /usr/lib32/libv4l
install -m 755 libv4l2.so.0 /usr/lib32
cd /usr/lib32 && \
	  ln -f -s libv4l2.so.0 libv4l2.so
install -m 755 v4l2convert.so.0 \
	  /usr/lib32/libv4l/v4l2convert.so
mkdir -p /usr/lib32/pkgconfig
install -m 644 libv4l2.pc /usr/lib32/pkgconfig
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/lib/libv4l2'
make -C libv4l1 install
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/lib/libv4l1'
mkdir -p /usr/include
install -p -m 644 ../include/libv4l1.h /usr/include
mkdir -p /usr/lib32/libv4l
install -m 755 libv4l1.so.0 /usr/lib32
cd /usr/lib32 && \
	  ln -f -s libv4l1.so.0 libv4l1.so
install -m 755 v4l1compat.so.0 \
	  /usr/lib32/libv4l/v4l1compat.so
mkdir -p /usr/lib32/pkgconfig
install -m 644 libv4l1.pc /usr/lib32/pkgconfig
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/lib/libv4l1'
make[1]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/lib'
make -C utils install
make[1]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/utils'
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/libv4l2util'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/libv4l2util'
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/decode_tm6000'
mkdir -p /usr/bin
install -m 755 decode_tm6000 /usr/bin
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/decode_tm6000'
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/keytable'
mkdir -p /usr/bin
install -m 755 ir-keytable /usr/bin
install -m 644 rc_maps.cfg.example /etc
install -m 755 -d /etc/rc_keymaps
install -m 644 rc_keymaps/* /etc/rc_keymaps
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/keytable'
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/rds'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/rds'
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/v4l2-compliance'
mkdir -p /usr/bin
install -m 755 v4l2-compliance /usr/bin
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/v4l2-compliance'
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/v4l2-ctl'
mkdir -p /usr/bin
install -m 755 cx18-ctl ivtv-ctl v4l2-ctl /usr/bin
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/v4l2-ctl'
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/v4l2-dbg'
mkdir -p /usr/sbin
install -m 755 v4l2-dbg /usr/sbin
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/v4l2-dbg'
make[2]: Entering directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/xc3028-firmware'
make[2]: Nothing to be done for `install'.
make[2]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/utils/xc3028-firmware'
# Test if libsysfs is installed
# Test whether qmake is installed, and whether it is for qt4.
make[1]: Leaving directory `/home/pif/Downloads/v4l-utils-0.8.1/utils'
root@pif-asus:/home/pif/Downloads/v4l-utils-0.8.1# 


I'll be damned I don't understand a thing.
Can someone point me in the right direction ?
I mean I tried following some advice some tutorials on the net about compiling but I always end up with some sort of errors or they give false instructions (for example one of it tells me to do ./configure , there's no configure in my directory ).

---

### Post by gandaran on 2010-10-14
any reason you have to compile this package?
cant you install it from the software center?
you need to install build-essentials to compile, do you have it?

---

### Post by petrasflorin on 2010-10-14
No idea what build-essentials is.
No such package in the repository.

---

### Post by Schrute Farms on 2010-10-14
Helpful page here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Toz on 2010-10-14
First of all, I don't see any error messages in the output. It looks like the compilation and installation worked fine. Not sure what this package does, but try running Video4Linux and see if the added functionality is there.

Secondly, following up on what gandaran said, if you open up a terminal window and type in:

apt-cache search libv4

you'll see:

libv4l-0 - Collection of video4linux support libraries
libv4l-dev - Collection of video4linux support libraries (development files)

a futher 'apt-cache policy libv4l-0' will give you info about the package. And 'sudo apt-get install libv4l-0' will install the package. I'm running 10.10 and the version in the repositories is 0.6.4 whereas the one you are trying to compile is 0.8.1 - not sure if that's relevant.

/ToZ

---

### Post by oldos2er on 2010-10-14
> **petrasflorin said:**
> No idea what build-essentials is.
No such package in the repository.

It's *build-essential*.

I agree with Toz, there are no errors in the output you've shown. Maybe you could tell us what your goal in installing this is?

---

### Post by petrasflorin on 2010-10-15
Yeah but this one was just an example, I was wondering if there are some... golden rules to follow when compiling or some... standard steps/commands/thing you need to do.

---

### Post by Toz on 2010-10-15
The first golden rule is don't compile unless you absolutely have to. Search the software centre or use apt-cache search from the command line to search the repositories for the package you want and install from there. If you absolutely need to compile, then the link that Shrute Farms mentioned ([https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)) is a good source of information.

---

### Post by oldos2er on 2010-10-15
Also [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

