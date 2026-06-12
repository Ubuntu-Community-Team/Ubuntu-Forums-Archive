---
title: "Virtualbox and Karmic problems"
date: 2010-01-15
forum: General Help
---

### Post by sr_guy on 2010-01-15
I'm trying to get virtualbox functional on my 9.10 karmic install but keep running into errors that it can't compile because of a kernel compatibility issue. I'm afraid that if I upgrade/downgrade the kernel I may end up with more broken apps.

Below is the error in /var/log/vbox-install.log

```


Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.1.2

------------------------------
Deleting module version: 3.1.2
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.1.2/source ->
                 /usr/src/vboxdrv-3.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.31-17-generic-pae cannot be found at
/lib/modules/2.6.31-17-generic-pae/build or /lib/modules/2.6.31-17-generic-pae/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


```

---

### Post by khelben1979 on 2010-01-15
Try this:
```
sudo apt-get install linux-source
```
to see if it solves your problem.

You have VirtualBox packages available [here]("http://www.virtualbox.org/wiki/Linux_Downloads") if you're interested, so you don't need to compile it yourself.

---

