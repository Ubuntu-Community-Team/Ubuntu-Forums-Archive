---
title: "A question about installing a driver."
date: 2012-02-17
forum: General Help
---

### Post by emptycoder on 2012-02-17
Hi everyone.
I want to install the new ATI AMD Catalyst 12.1 Driver and I have found these steps to do that:

To install ATI AMD Catalyst 12.1 Driver under Ubuntu 11.10/11.04, remove first the old driver with these commands:

** sudo sh /usr/share/ati/fglrx-uninstall.sh**
** sudo apt-get remove –purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx**

Then run the following commands to start the installation of the driver:

**cd ~/; mkdir catalyst12.1; cd catalyst12.1/**
**wget -O amd-driver-installer-12-1-x86.x86_64.run [http://goo.gl/bHxHw](http://goo.gl/bHxHw)**
**chmod +x amd-driver-installer-12-1-x86.x86_64.run**
[B]sh ./amd-driver-installer-12-1-x86.x86_64.run

[/B]I remember that I installed an ATI Driver without removing the old one, is it safe to remove old drivers first? and what if something goes wrong, how do I resotre the old open-source driver on Recovery mode? what are the commands?
I have many important things on my system and I don't want to miss up with anything then find myself formatting and installing the whole OS.

Thanks a lot.

---

### Post by forestG on 2012-03-18
There will be no problem if you uninstall the drivers. If afterwards you have problems when you startup the computer then before putting username and password press ctrl-alt-f1 and then login to the terminal-screen that will appear. There you can write sudo apt-get install ubuntu-desktop and you will get all packages of ubuntu. More inforamation on the site ubuntu-psychocats [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/).

---

### Post by Mark Phelps on 2012-03-19
> **emptycoder said:**
> ...I remember that I installed an ATI Driver without removing the old one, is it safe to remove old drivers first? and what if something goes wrong, how do I resotre the old open-source driver on Recovery mode? what are the commands?

Instructions are in the link below:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

> I have many important things on my system and I don't want to miss up with anything then find myself formatting and installing the whole OS.
Then basically, leave them alone.  Unless there is some critical feature you need in the newer ATI drivers, there is no value to upgrading them.

---

