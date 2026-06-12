---
title: "On Ubuntu 10.04 installation, bcmwl driver not working"
date: 2010-05-01
forum: General Help
---

### Post by xtremeshredder on 2010-05-01
hello, i have just installed Ubuntu 10.04 LTS on my Dell XPS M1530. Previously, i got the bcmwl proprietary driver to work when i was trying the live cd. for some reason, when i installed it however, it did not work the same. when ubuntu booted when i installed it, it did not sense the proprietary driver. so i went in to the ubuntu disc itself and got the bcmwl driver and the dkms packages. so i try to install both of them with dpkg -i as root. dkms installed successfully, however, the bcmwl driver gave me this:

root@Ryan-PC:/home/ryan/Desktop# dpkg -i bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb
(Reading database ... 122807 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3 (using bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--install):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-source
root@Ryan-PC:/home/ryan/Desktop# 

why is it doing this, can anyone help?



EDIT: output after sudo apt-get install patch
[FONT=monospace]
[/FONT]root@Ryan-PC:/home/ryan# sudo apt-get install patch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package patch is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package patch has no installation candidate
root@Ryan-PC:/home/ryan#

---

### Post by onyxrev on 2010-05-02
You could try some of the suggestions here:

[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

I had a similar problem in that I needed the kernel headers (and build-essential apparently wasn't enough).

---

### Post by nbulchandani on 2010-05-02
hello ,
i am getting the same errors..can anyone tell me the fix in simple language.
Thanks

---

### Post by night Wolfenstein ET on 2010-05-12
Problem
-------
While running the "Ubuntu 10.04" live cd I could activate the "bcmwl" driver from: System/Administration/Hardware Drivers ==> Broadcom STA wireless driver
And I could connect to my wireless network.

But after install "Ubuntu 10.04" when I go to: System/Administration/Hardware Drivers. The "Broadcom STA wireless driver" did not appear and the computer couldn't find any wireless network.

Related: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/441492](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/441492)


Solution
--------
- Open Synaptic Pacakage Manager and search: bcmwl
if the bcmwl-kernel-source package is installed remove it.

- Download (you can use the live cd):
    fakeroot_1.14.4-1ubuntu1_i386.deb
    patch_2.6-2ubuntu1_i386.deb
from Ubuntu packages ([http://packages.ubuntu.com/](http://packages.ubuntu.com/))

- Install the downloaded packages:
    $ sudo dpkg -i patch*
    $ sudo dpkg -i fakeroot*

- Put the ubuntu 10.04 "live cd" in CD drive and open Synaptic

- Go to: "Settings/Repositories/Ubuntu Software", check the installable from CD-ROM/DVD option and close the "Software Sources" window.

- Click the reload button on Synaptic, search: bcmwl and install the bcmwl-kernel-source package.

- Reboot the computer and go to: System/Administration/Hardware Drivers and activate Broadcom STA wireless driver

---

### Post by sbryant31 on 2010-11-27
Thank you for the advice but I dont have a CD drive, so should i put livecd on a flash drive? Also, will the installation cd for the netbook remix work?

---

