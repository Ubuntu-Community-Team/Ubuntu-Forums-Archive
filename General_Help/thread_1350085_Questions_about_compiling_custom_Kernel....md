---
title: "Questions about compiling custom Kernel..."
date: 2009-12-08
forum: General Help
---

### Post by Falkor on 2009-12-08
Hi everybody,

----------------------------
([link]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.31.6.tar.gz")) Kernel: linux-2.6.31.6.tar.gz
([link]("http://www.kernel.org/pub/linux/kernel/projects/rt/patch-2.6.31.6-rt19.gz")) Patch: patch-2.6.31.6-rt19.gz
----------------------------

I am trying to compile a custom Kernel, using the above two files found on kernel.org, and I am following this guide:

----------------------------
([link]("https://help.ubuntu.com/community/Kernel/Compile")) Ubuntu Documentation > Community Documentation > KernelCompile > Alternate Build Method: The Old-Fashioned Debian Way
----------------------------

I am confused about this step:

----------------------------
sudo apt-get install [COLOR=Red]linux-source[/COLOR]
mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-<version-number-here>.tar.bz2
cd linux-source-<version-number-here>
----------------------------

Is that regardless of which version I use (as mentioned, it is linux-2.6.31.6), I have to install that [COLOR=Red]linux-source[/COLOR] package?

When I searched with aptitude, I found:

----------------------------
linux-source
linux-source-2.6.28 // This package is mainly meant for other packages to use, in order to build custom flavours.
----------------------------

The file linux-2.6.31.6.tar.gz which I got from kernel.org, is it the same type of package as the linux-source-2.6.28?


Thanks.

---

### Post by Falkor on 2009-12-09
Also, I would like to ask:

1)
I used to compile and install custom Kernel by doing:

-----------------------------
make menuconfig
make clean
make bzImage
make modules
make modules_install
make install
-----------------------------

and for 2.6.31.6-rt19 as mentioned in my above post, for removing that custom kernel, I just need to delete the following:

-----------------------------
/boot/config-2.6.31.6-rt19
/boot/initrd.img-2.6.31.6-rt19
/boot/System.map-2.6.31.6-rt19
/boot/vmcoreinfo.img-2.6.31.6-rt19
/boot/vmlinuz-2.6.31.6-rt19

/lib/modules/2.6.31.6-rt19/
-----------------------------

and in case I reinstall Ubuntu (with no change of hardwares), I could backup and reuse those files, but are these a correct ways for removing and backing up custom Kernel? (It works for me somehow...)

2)
If I followed the approach for Intrepid, Jaunty, and Karmi, mentioned in the community documentation ([link]("https://help.ubuntu.com/community/Kernel/Compile")), what should I do for removing and backing up the custom Kernel then?

3)
One more question, that the last part of the above community documentation, mentions about rebuilding linux-restricted-modules. Is that a required step for using a custom Kernel?


Thanks.

---

