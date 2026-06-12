---
title: "NVIDIA installer can't find kernel source"
date: 2010-03-07
forum: General Help
---

### Post by lakersforce on 2010-03-07
First my uname -a
```
Linux quad 2.6.33 #1 SMP Sun Mar 7 18:22:02 CET 2010 x86_64 GNU/Linux
```

I am using Trisquel GNU/Linux 3.0. I am asking my questions here, since this involves non-free drivers. I succesfully installed the nvidia driver on the default kernel. But the default kernel has removed all support for DVB USB sticks, so I had to compile my own kernel.

I got the newest version from kernel.org. Saved the archieve to /usr/src/. unzipped the file in the directory (so my kernel source is now in /usr/src/linux-2.6.33/.) Made a symlink with ln -s linux-2.6.33 linux. I compiled the kernel succesfully. Did a "make install" and "make modules_install" and ran "update-grub". Restarted system. Cd'ed to my source directory and ran "make headers_install" succesfully. Looking at my timestamps, it looks like the kernel headers has been installed to /usr/src/linux-2.6.33/usr/include/linux/.

I downloaded the latest x86_64 drivers from nvidias website. Went to console 1 and closed up X.

If I start the installer without any parameters (sh NVIDIA*.run) I get the following error:

```
ERROR: Unable to determine the version of the kernel sources located in
       '/lib/modules/2.6.33/source'.  Please make sure you have installed the
       kernel source files for your kernel and that they are properly
       configured; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' or 'kernel-devel' RPM installed.  If you know the
       correct kernel source files are installed, you may specify the kernel
       source path with the '--kernel-source-path' command line option.
```
/lib/modules/2.6.33/source is a symlink which point to /usr/src/linux-2.6.33

I get the same error if using --kernel-source-path=/usr/src/linux/, /usr/src/linux-2.6.33/ and similar options which link to this directory through symlinks.

If I use --kernel-source-path=/usr/src/linux-2.6.33/usr/include, I get the following error:

```
ERROR: The kernel header file
       '/usr/src/linux-2.6.33/usr/include/include/linux/kernel.h' does not
       exist.  The most likely reason for this is that the kernel source path
       '/usr/src/linux-2.6.33/usr/include' is incorrect.
etc.
```

OK, that makes sense, I think to myself, since the headers file (and the *.h file referred to) are not in /usr/src/linux-2.6.33/usr/include/include/linux/ but /usr/src/linux-2.6.33/usr/include/linux/

I then ran the installer with --kernel-source-path=/usr/src/linux-2.6.33/usr/ but got the following error:

```
ERROR: Unable to determine the version of the kernel sources located in
       '/usr/src/linux-2.6.33/usr/'.  Please make sure you have installed the
       kernel source files for your kernel and that they are properly
       configured;
```

What am I missing? Why can't the installer find the sources? I triple checked all my symlinks in /usr/src/ and /lib/modules/ and they all point at the appropiate places.

---

### Post by flippo on 2010-03-07
I've had a similar issue when using a brand new kernel without a brand new .run file.  Did you download a new .run file (not just newest version, but actually new file)?  I have the nvidia working on my gentoo setup (using 2.6.33) with driver version 190.53.

---

### Post by lakersforce on 2010-03-07
I am not sure what you are asking, but my files name is NVIDIA-Linux-x86_64-190.53-pkg2.run

---

### Post by lakersforce on 2010-03-08
/bumb

The .run file is also original i.e. unaltered.

---

### Post by oldos2er on 2010-03-08
You need to install the package nvidia-190-kernel-source

---

### Post by lakersforce on 2010-03-08
Thanks for the suggestions, but as I wrote in my OP I am using Trisquel (a Ubuntu derivative) and all nvidida related packages is not aviable (after all, if it were I would use the default package and not attempt a custom driver install.) And also I can't use any packages from the repository, since I am using a custom kernel.

And I also have the (vanilla from kernel.org) kernel source and kernel headers installed. Question is, what am I missing?

---

### Post by lakersforce on 2010-03-08
Thanks to the guys over at LQ I solved it.

Turns out that the structure of the 2.6.33 kernel has been changed and the Nvidia installer program therefore has to be [patched]("http://www.nvnews.net/vbulletin/showpost.php?p=2164440&postcount=20").

---

### Post by AldenIsZen on 2012-03-25
Lakersforce, still running a similar setup? I'd be interested in what you're using if you have a more current Trisquel install. I am considering doing the same and using the proprietary driver.

---

### Post by oldos2er on 2012-03-25
Closed, necromancy.

From the posting guidelines: "If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

