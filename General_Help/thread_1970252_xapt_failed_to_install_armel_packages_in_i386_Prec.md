---
title: "xapt failed to install armel packages in i386 Precise"
date: 2012-05-01
forum: General Help
---

### Post by cnxsoft on 2012-05-01
In oneric, I could use xapt to install armel packages in my 32-bit Ubuntu desktop installation.
Now that I have upgraded to Ubuntu Precise it returns an warnings and errors:

> sudo xapt  -a armel -M [http://ports.ubuntu.com](http://ports.ubuntu.com) -S precise libbz2-dev

....

Use of qw(...) as parentheses is deprecated at /usr/bin/dpkg-cross line 1053.
dpkg-cross: Skipping Multi-Arch package 'libbz2-1.0_1.0.6-1_armel.deb'.
Use of qw(...) as parentheses is deprecated at /usr/bin/dpkg-cross line 1053.
dpkg-cross: Skipping Multi-Arch package 'libc6_2.15-0ubuntu10_armel.deb'.

....

Unpacking replacement debconf-armel-cross ...
dpkg: error processing /var/lib/xapt/output/dpkg_1.16.1.2ubuntu7_armel.deb (--install):
 package architecture (armel) does not match system (i386)
Preparing to replace dpkg-armel-cross 1.16.1.2ubuntu7 (using .../dpkg-armel-cross_1.16.1.2ubuntu7_all.deb) ...
Unpacking replacement dpkg-armel-cross ...



If I add -m, it won't skip the package, but still fail to install the lib.

Is it a bug or a misconfiguration of multiarch ?

---

### Post by cnxsoft on 2012-05-03
I've been told it was a bug so I filled it here: [https://bugs.launchpad.net/ubuntu/+source/emdebian-crush/+bug/992503](https://bugs.launchpad.net/ubuntu/+source/emdebian-crush/+bug/992503)

Instead, I'm now using multiarch as I explain @ [http://www.cnx-software.com/2012/05/02/getting-started-with-multiarch-armel-armhf-in-ubuntu/](http://www.cnx-software.com/2012/05/02/getting-started-with-multiarch-armel-armhf-in-ubuntu/)

---

