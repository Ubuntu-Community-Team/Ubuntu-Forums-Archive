---
title: "Updated nvidia no compiz now. (Illegal instruction)"
date: 2012-02-15
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-02-15
am on lucid and i just updated to nvidia 295.20 and i lost compiz
the driver is active

if i click on "OpenGL/GLX Information" in nvidia settings the app crashes
```
~$ compiz --replace
Illegal instruction
```running ubuntu 10.04 everything is upto date

i am using this ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")


Edit just ran this:
```
sudo dpkg-reconfigure nvidia-current
[sudo] password for chad: 
Removing all DKMS Modules
Done.
update-initramfs: Generating /boot/initrd.img-2.6.35-32-generic
Loading new nvidia-current-295.20 DKMS files...
Building only for 2.6.35-32-generic
Building for architecture x86_64
Building initial module for 2.6.35-32-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-32-generic/updates/dkms/

depmod....

DKMS: install Completed.
```and rebooted 
no change
if not for my xorg.conf i don't even get a useable resolution...

edit: reinstalled nvidia-current and nvidia-current-modaliases package in synaptic

```
(Reading database ... 260642 files and directories currently installed.)
Preparing to replace nvidia-current 295.20-0ubuntu1~lucid~xup1 (using .../nvidia-current_295.20-0ubuntu1~lucid~xup1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Preparing to replace nvidia-current-modaliases 295.20-0ubuntu1~lucid~xup1 (using .../nvidia-current-modaliases_295.20-0ubuntu1~lucid~xup1_amd64.deb) ...
Unpacking replacement nvidia-current-modaliases ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up nvidia-current (295.20-0ubuntu1~lucid~xup1) ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-295.20 DKMS files...
Building only for 2.6.35-32-generic
Building for architecture x86_64
Building initial module for 2.6.35-32-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-32-generic/updates/dkms/

depmod....

DKMS: install Completed.

Setting up nvidia-current-modaliases (295.20-0ubuntu1~lucid~xup1) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-32-generic
Processing triggers for python-support ...
```
EDIT:
HOLY crap this is a 1st, a windows solution (reinstall) actually worked !!!!!!!!

---

