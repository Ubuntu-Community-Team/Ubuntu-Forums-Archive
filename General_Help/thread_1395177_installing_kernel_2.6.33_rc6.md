---
title: "installing kernel 2.6.33 rc6?"
date: 2010-01-31
forum: General Help
---

### Post by sdowney717 on 2010-01-31
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc6/)

How would you install this kernel in karmic?
I get nvidia  and vbox fail errors

I am currently using nvidia 195 driver and this wants to install 190 driver.

---

### Post by darco on 2010-01-31
I just posted this link in another thread a few mins ago....
go here for instructions:

[http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

Then here for the kernel

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc6/)

The first link is just a guide, dont click the actual kernel links


darco

---

### Post by sdowney717 on 2010-01-31
still failing rc6 does samething

> Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.33-020633rc2-generic                                                                                   
 *  nvidia (190.53)...                                                          nvidia (190.53): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxdrv (3.0.10)...                                                         vboxdrv (3.0.10): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxnetadp (3.0.10)...                                                      vboxnetadp (3.0.10): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxnetflt (3.0.10)...                                                      vboxnetflt (3.0.10): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Errors were encountered while processing:
 linux-headers-2.6.33-020633rc2-generic


---

### Post by bakegoodz on 2010-01-31
The programs you mentioned build there own kernel modules. These types of programs often have to be updated for new kernels. They make updates to be compatible with kernels in major distros releases. So in summery a release candidate kernel is too new to be supported by commercial software that has it's own kernel modules.

---

### Post by Vladimir Hidalgo on 2010-02-19
So Nvidia VGA users can't test kernel latest RC releases without applying patches and things alike?.

I saw this:
[http://www.nvnews.net/vbulletin/showthread.php?t=142794](http://www.nvnews.net/vbulletin/showthread.php?t=142794)

But I guess it's too much work for having the kernel latest version and not being a kernel hacker.

---

