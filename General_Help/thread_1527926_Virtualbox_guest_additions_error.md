---
title: "Virtualbox guest additions error"
date: 2010-07-09
forum: General Help
---

### Post by akernan on 2010-07-09
I'm using Virtualbox to test Meerkat.  I have the same problem with Ubuntu & Xubuntu,

Here is the output from VBoxLinuxAdditions-x86.run..

Verifying archive integrity... All good.
Uncompressing VirtualBox 3.1.6 Guest Additions for Linux........
VirtualBox Guest Additions installer
Removing installed version of VirtualBox Guest Additions...
Building the VirtualBox Guest Additions kernel modules
Building the main Guest Additions module ...done.
Building the shared folder support module ...fail!
(Look at /var/log/vboxadd-install.log to find out what went wrong)
Installing the Window System drivers
Warning: unknown version of the X Window System installed.  Not installing
X Window System drivers.
Installing graphics libraries and desktop services components ...done.


Here's the last few lines from vboxadd-install.log..

make[2]: *** [/tmp/vbox.0/regops.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxvfs] Error 2

Can anyone help?

---

### Post by Leppie on 2010-07-09
have you tried with virtualbox 3.2.6?

---

### Post by akernan on 2010-07-09
No.  I'm using Virtualbox-ose.

---

### Post by Leppie on 2010-07-09
try the puel edition, they're both free. the only difference is that the puel isn't open source.

---

### Post by akernan on 2010-07-09
Sorry, I tried installing Virtualbox-3.2.6 and it didn't work.  Said something about not an application.  What is puel edition?

---

### Post by Leppie on 2010-07-09
> **akernan said:**
> Sorry, I tried installing Virtualbox-3.2.6 and it didn't work.  Said something about not an application.  What is puel edition?
[VirtualBox Personal Use and Evaluation License (PUEL)]("http://www.virtualbox.org/wiki/VirtualBox_PUEL")
add the repo from this page: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by akernan on 2010-07-10
I upgraded to Virtualbox 3.2.6.  It helps when I use the right command.  Thanks for the help.

---

### Post by Leppie on 2010-07-10
you're welcome, glad it's working :)

---

### Post by jayachandranm on 2010-09-16
A related post to fix issues for maverick virtual machine.

[http://www.unixmen.com/linux-tutorials/1157-install-guest-addition-in-ubuntu-1010-maverick-meerkat-fix#josc2527](http://www.unixmen.com/linux-tutorials/1157-install-guest-addition-in-ubuntu-1010-maverick-meerkat-fix#josc2527)

Referenced in lifehacker page,
[http://lifehacker.com/5633811/fix-virtualboxs-guest-additions-in-ubuntu-1010](http://lifehacker.com/5633811/fix-virtualboxs-guest-additions-in-ubuntu-1010)

Jaya

---

