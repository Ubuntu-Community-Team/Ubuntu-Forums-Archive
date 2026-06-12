---
title: "How do I tell Virtualbox where my custom kernel is?"
date: 2009-11-25
forum: General Help
---

### Post by humphreybc on 2009-11-25
I'm using kernel 2.6.32-020632rc5-generic because it enables 3D using the open source ATI driver.

Unfortunately, the Vbox kernel module can't install:

```

benjamin@benjamin-laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong

```

And the log says:

```

Error! Your kernel source for kernel 2.6.32-020632rc5-generic cannot be found at
/lib/modules/2.6.32-020632rc5-generic/build or /lib/modules/2.6.32-020632rc5-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

I'm not sure how to tell DKMS where it's located... can someone help me out please?

Also, how do I update my kernel to a newer version? I've noticed that rc8 is out now. I remember installing 32rc5 was as easy as downloading a .deb package, but I can't seem to find one for the rc8 kernel at [www.linux.org](www.linux.org)

Thanks

---

