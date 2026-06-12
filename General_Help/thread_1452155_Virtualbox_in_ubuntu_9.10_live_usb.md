---
title: "Virtualbox in ubuntu 9.10 live usb"
date: 2010-04-11
forum: General Help
---

### Post by benmayim on 2010-04-11
I've used lili to make a bootable ubuntu 9.10. on a USB flash drive. It works fine, persists, etc.

In the following, I'm not talking about the virtual box that comes with the live .iso image, I'm talking about the program called "virtual box" that allows a person to run programs from other systems. My base system is Linux, and it is on a bootable USB flash drive, and I want to make a virtualbox to run some windows programs

I've downloaded the .deb package for virtualbox for ubuntu 9.10 from the virtualbox website, and the first time I tried to install, it started installing, said it needed to download some more packages, which it did, then proceeded on and eventually, everything disappeared on the desktop, except for the background, and just hung there.

I rebooted, and tried again, and when I activated the .deb file by clicking on it to start the installation again, the screen just flashed and did nothing more. The desktop and system remained normal, but I never ended up with virtualbox installed.

I'm NEW to linux, don't know much, and need to find out, if the reason it won't install is because it's on a live USB stick, or just doesn't work in Ubuntu 9.10. If it generally does work in ubuntu 9.10, then I'm guessing the fact it's on a bootable usb flash drive has something to do with the problem, and I need to find out what to do to get virtualbox to install on my linux usb flash system.

---

### Post by foobar66 on 2010-04-11
Login as root, then do:

> dpkg -i virtual*.deb

After installation of the package:

> /etc/init.d/vboxdrv setup

Then try again to use VirtualBox.

---

### Post by wilee-nilee on 2010-04-11
Make sure you have dkms installed in synaptic or through the terminal and then look at the deb, when I installed Vbox it showed a needed dependency on the deb gui, I forget what it was though.

---

### Post by benmayim on 2010-04-11
I started over with making my usb live ubuntu 9.10 from Lili and now vbox installed.

MY POST IS SOLVED, but I don't know how to indicate that other than this reply.

---

