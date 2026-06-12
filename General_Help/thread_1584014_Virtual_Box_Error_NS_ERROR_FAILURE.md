---
title: "Virtual Box Error NS_ERROR_FAILURE"
date: 2010-09-28
forum: General Help
---

### Post by shwndzzl on 2010-09-28
Seems this happened after an update not sure what was updated.
I open up Virtual Box 3.2.8 and try to start my virtual machine.

First I get this error: "Result Code: NS_ERROR_FAILURE (0x80004005)"
Then this comes up immediately after: "Kernel driver not installed ( rc=-1908 )

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."


I went to the Terminal and entered the command... 
"/etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         /etc/init.d/vboxdrv: 378: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong"

So i take the advice and enter: "/var/log/vbox-install.log" 
Then I get:" bash: /var/log/vbox-install.log: Permission denied"

Man i really dont know what to do here. Been using linux for about a month now.. still learning my way around, but the linux language just doesn't make any sense to me yet.

thanks...!!

---

### Post by prop99 on 2010-09-30
You should use:

 **sudo** /etc/init.d/vboxdrv setup

---

