---
title: "linux-rt image and headers in Lucid do not match source"
date: 2010-06-11
forum: General Help
---

### Post by Invalid Opcode on 2010-06-11
The binaries and headers that get installed by linux-image-rt and linux-headers-rt are not consistent with the source package for the kernel

By source package, I mean the source tree and realtime patches that are applied when I do:

$ apt-get source linux-image-2.6.31-10-rt

If you just do a diff between the include directories, there are over 101 changed files:

$ cd linux-rt-2.6.31
 $ diff -rq include /lib/modules/2.6.31-10-rt/build/include | wc -l
101


If I copy the /boot/config-2.6.31-10-rt file into the source and make oldconfig, there are a bunch of new options which should not be if the source was the same:

$ cd linux-rt-2.6.31
$ cp -vi /boot/config-2.6.31-10-rt .config
$ make oldconfig

[a bunch of new kernel options area asked for]

A further note is that the linux-rt source does not include the debian directory that is used to build the Ubuntu packages.

So how am I supposed to recreate the linux-rt binaries from source so  that the resultant output matches what comes in the linux-rt package?  

Thanks

---

### Post by Invalid Opcode on 2010-06-15
This turned out to be a sequence of operator errors and issues:

The first was running a 'make distclean' which deletes the 'debian' directory from the Ubuntu linux-rt source tree.

The second was not manually applying the -rt patches.  The "apt-get source" only extracts and applies the kernel source, not the actual -rt changes. 


So the proper sequence of events is:

$ apt-get source linux-image-2.6.31-10-rt
$ cd linux-rt-2.6.31
$ fakeroot debian/rules apply-patchset
$ cp /boot/config-2.6.31-10-rt .config
$ make oldconfig
$ make

You could also try building the kernel the Ubuntu/Debian way if you so choose.

Hopefully this helps anybody else trying to do this same thing.

---

