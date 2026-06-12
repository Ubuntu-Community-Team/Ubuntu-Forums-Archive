---
title: "virtualbox upgrade issues with maverick"
date: 2010-10-26
forum: General Help
---

### Post by quackeroni_pizza on 2010-10-26
Hi,

I recently upgraded to Maverick and keep seeing the following error when trying to run Virtualbox

> Kernel driver not installed (rc=-1908)


When I try to recompile the kernel driver, I get the following

> >>> sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Your kernel headers for kernel 2.6.32-22-generic cannot be found at
/lib/modules/2.6.32-22-generic/build or /lib/modules/2.6.32-22-generic/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong


---

### Post by SeijiSensei on 2010-10-26
Install the kernel-headers package that matches your kernel version:

```
sudo apt-get install linux-headers-$(uname -r)
```

> Error! Your kernel headers for kernel 2.6.32-22-generic cannot be found at
/lib/modules/2.6.32-22-generic/build or /lib/modules/2.6.32-22-generic/source.

My Maverick is up-to-date and uses kernel-headers-2.6.35-22-generic.  You're a couple of minor versions behind it appears.  I'd suggest "sudo apt-get upgrade" to begin with before getting the kernel headers and re-installing VirtualBox.

When you've finished upgrading and installing the kernel headers, you'll find the headers in /usr/src/linux-headers-2.6.35-22-generic and a symbolic link to this directory from /lib/modules/2.6.35-22-generic/build.

---

### Post by quackeroni_pizza on 2010-10-26
Yes I have done the apt-get upgrade but I stay stuck at 2.6.32

When I try to download kernel headers, I see this->


> >>> sudo apt-get install kernel-headers-$(uname -r)  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kernel-headers-2.6.32-22-generic
E: Couldn't find any package by regex 'kernel-headers-2.6.32-22-generic'


---

### Post by SeijiSensei on 2010-10-26
> **quackeroni_pizza said:**
> Yes I have done the apt-get upgrade but I stay stuck at 2.6.32

When I try to download kernel headers, I see this->

Sorry, it should have read **linux-headers**, not kernel-headers.  I must have misread something in the output of dpkg on my system.

Still 2.6.32-22-generic is a Lucid package; the Maverick package is at 2.6.35.  When you boot, how many kernels does grub offer you?  Which one are you running?

---

### Post by quackeroni_pizza on 2010-10-27
Weird.. The largest version I see is 2.6.32 in grub. I just did an upgrade from Lucid and hoped it would take care of doing a smooth upgrade. Everything in sources.list points to Maverick.

Now how to I upgrade the kernel?

---

### Post by quackeroni_pizza on 2010-10-27
Ok, I manually added a 2.6.35 line in the boot menu.

Now the simple "/etc/init.d/vboxdrv setup" works fine. I can run virtualbox just fine.

Still not sure why 2.6.35 never made it into grub menu.. I even tried a grub update.

---

