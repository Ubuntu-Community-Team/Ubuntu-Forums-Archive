---
title: "KernelHowto"
date: 2006-03-15
forum: General Help
---

### Post by jonnight on 2006-03-15
Hello, 

I am following a manual KernelHowto from the Ubuntu web,  

and at the very begining ,

Preparation

_You will need the build-essential fakeroot and kernel-package packages, to build a kernel._

**bash:~$ sudo apt-get install build-essential fakeroot kernel-package**

0 update, 0 will install, 0 to delete y 0 no updated.


_You will need the gcc-3.4 compiler for 2.6 series kernels_

**bash:~$ sudo apt-get install gcc-3.4**

E: cant find the paquet gcc-3.4


Yo_u will need developer libraries for the kernel configuration tools_
[B]
bash:~$ sudo apt-get install libqt3-mt-dev libncurses-dev[/B]

E: cant find the paquet libqt3-mt-dev



please, help, how can I get this , and what do I have to do to install them ??

thanks

---

### Post by maulattu on 2006-03-16
sudo adept

and from that window you can look for those packets ;)

---

### Post by tqiw on 2006-03-16
not sure, but think you might have to enable these repositories to get gcc
[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

