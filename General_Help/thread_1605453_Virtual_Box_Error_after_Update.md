---
title: "Virtual Box Error after Update"
date: 2010-10-25
forum: General Help
---

### Post by Lamez on 2010-10-25
First, let me say this: I have checked the known issues and the sticky post, it does not seem to be related. I have Ubuntu as my host OS and I want to run Windows as a guest. 

Now, Here is the error:
> 
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


I have done the obvious:
> 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install dkms
sudo /etc/init.d/vboxdrv setup

I still have the same error. I just updated from Ubuntu 10.04 to 10.10, then I was prompted by virtual box to update to the newest version, then this happened. I have also googled the problem, no help really.

Any thought?

---

### Post by SeijiSensei on 2010-10-25
Try "sudo apt-get install build-essential" then rerun /etc/init.d/vboxdrv setup.  You may be missing some required packages to build software from source.

---

### Post by Lamez on 2010-10-25
No luck: sudo: /etc/init.d/vboxdrv: command not found

---

