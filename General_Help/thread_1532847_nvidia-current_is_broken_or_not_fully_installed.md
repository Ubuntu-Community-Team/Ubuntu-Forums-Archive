---
title: "nvidia-current is broken or not fully installed"
date: 2010-07-17
forum: General Help
---

### Post by ibrahim.k on 2010-07-17
Hi,

I was installing nvidia drivers for my laptop

Hp-pavilion 1045ee

but something wrong happened during the installation.

and now i don't know hot to install it or remove the broken package cause I get this 
nvidia-current is broken or not fully installed

and can you please tell me how to install the latest version of nvidia drivers ?

bests.

ibrahim@ibrahim-laptop:~$ sudo apt-get install --reinstall nvidia-current && sudo dpkg-reconfigure nvidia-curren
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B/40.8MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 176079 files and directories currently installed.)
Preparing to replace nvidia-current 195.36.24-0ubuntu1~10.04 (using .../nvidia-current_195.36.24-0ubuntu1~10.04_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Processing triggers for man-db ...
Setting up nvidia-173 (173.14.22-0ubuntu11) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up nvidia-current (195.36.24-0ubuntu1~10.04) ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-195.36.24 DKMS files...
Building only for 2.6.32-22-generic
Building for architecture x86_64
Building initial module for 2.6.32-22-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/

depmod....

DKMS: install Completed.

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-173
E: Sub-process /usr/bin/dpkg returned an error code (1)
ibrahim@ibrahim-laptop:~$

---

### Post by ibrahim.k on 2010-07-31
help me guys

---

### Post by stinkeye on 2010-07-31
Don't know what went wrong but this is how I installed the latest nvidia drivers for GeForce 6 and above cards.
[**_[COLOR="DarkRed"]How To Install nVidia 256.35 Display Drivers In Ubuntu (From A PPA Repository)[/COLOR]_**]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html")

---

### Post by ibrahim.k on 2010-08-03
It did not work, thnx anyway

---

### Post by basotl on 2011-05-03
Was searching and ran across this way later. For future note you left the "t" off the reconfigure command.

"sudo dpkg-reconfigure nvidia-curren"

---

