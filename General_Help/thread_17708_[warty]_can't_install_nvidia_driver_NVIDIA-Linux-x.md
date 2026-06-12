---
title: "[warty] can't install nvidia driver NVIDIA-Linux-x86-1.0-6629-pkg1.run"
date: 2005-03-02
forum: General Help
---

### Post by Liquid Crystal on 2005-03-02
Hello everyone,

I'm using kernel 2.6.8.1-3-386
I just downloaded the nvidia driver named "NVIDIA-Linux-x86-1.0-6629-pkg1.run" from nvidia.com
according to their README. It asks to run the installer and it should do the job!
However, I get stuck when it says:

-> Performing CC test with CC="cc".
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.

       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the appropriate nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)

Any hints? #-o

---

### Post by carney1979 on 2005-03-02
Try this:

first in a terminal or tty, do a:

uname -r

it will return something like:

2.6.10-4-386

Then try to run your Nvidia run package with (from the folder the run package is in):

./NVIDIA*.run -k 2.6.10-4-386 (or whatever uname -r returned).

I had a problem in that the 6629 Nvidia driver would build right, but it would lock up at the Nvidia splash screen. This is due to a bug in the 6629 driver that makes it incompatible with TNT2 cards and (at least) my Geforce MX4 card.

So I had to revert to the 6111 driver and it for some reason couldn't find my kernel sources or headers like the 6629 version could.

So I had to build mine like the above example.

Unfortunately, I had to do all this just this morning from work while on a break and I'm forced to run an NT machine at work, so I can't test the module to see if it works until I get home......

Best of luck!

David

---

### Post by Liquid Crystal on 2005-03-05
Hello carney1979,

Unfortunately, it didn't work with me. It gave me the same error posted earlier!

What do you think? Is there any other way of trying ot or shall I try an older driver? :cry:

---

### Post by carney1979 on 2005-03-13
Uhh...

How about trying the new driver Nvidia just released yesterday or the day before?

It worked for me.

Note: If you have a package named nvidia-glx installed, you will want to remove it or you will be rebuilding Nvidia's module every time you boot up.

David

---

