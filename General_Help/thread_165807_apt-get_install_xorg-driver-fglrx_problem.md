---
title: "apt-get install xorg-driver-fglrx problem"
date: 2006-04-25
forum: General Help
---

### Post by akoylini on 2006-04-25
Hello to all of you,so i try to install fglrx but i take this error:
$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-driver-fglrx



whats going wrong?
:(

---

### Post by dg_w on 2006-04-25
What repos have you got in the /etc/apt/sources.list file

Un comment the universe and add

## PLF repo's.
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

sudo apt-get update
sudo apt-get dist-upgrade

reboot (if kernel is updates)
sudo apt-get install xorg-driver-fglrx

---

### Post by shuttleworthwannabe on 2006-04-25
I am sure u have checked u are connected to the net?? and read these [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Have u tried the synatptic route?

Also I am sure ati driver is in main repo??? try opeing the universe and multiverse repo's just in case.

good luck

---

