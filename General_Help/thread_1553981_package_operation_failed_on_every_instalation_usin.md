---
title: "package operation failed on every instalation using ubuntu software center"
date: 2010-08-15
forum: General Help
---

### Post by omgwtf1337 on 2010-08-15
Slightly New user of Ubuntu 10.4

It doesn't seem to matter what i try and install or uninstall all lead to similar error messages. 
(TRYING TO INSTALL I GET)

installArchives() failed: Selecting previously deselected package xaw3dg. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 153795 files and directories currently installed.) 
Unpacking xaw3dg (from .../xaw3dg_1.5+E-17build1_i386.deb) ... 
Selecting previously deselected package 3dchess. 
Unpacking 3dchess (from .../3dchess_0.8.1-16_i386.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for menu ... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up userful-multiplier (341-20090901000926-0ubuntu1) ... 
Section "ubuntu 10.04" is not exist. 
(EE) Not supported linux system 
dpkg: error processing userful-multiplier (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up xaw3dg (1.5+E-17build1) ... 
 
Setting up 3dchess (0.8.1-16) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for menu ... 
Errors were encountered while processing: 
 userful-multiplier 
Setting up userful-multiplier (341-20090901000926-0ubuntu1) ... 
Section "ubuntu 10.04" is not exist. 
(EE) Not supported linux system 
dpkg: error processing userful-multiplier (--configure): 
 subprocess installed post-installation script returned error exit status 1 


(REMOVING SOFTWARE I GET THIS)
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 153805 files and directories currently installed.) 
Removing achilles ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
Processing triggers for python-support ... 
Setting up userful-multiplier (341-20090901000926-0ubuntu1) ... 
Section "ubuntu 10.04" is not exist. 
(EE) Not supported linux system 
dpkg: error processing userful-multiplier (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 userful-multiplier 
Setting up userful-multiplier (341-20090901000926-0ubuntu1) ... 
Section "ubuntu 10.04" is not exist. 
(EE) Not supported linux system 
dpkg: error processing userful-multiplier (--configure): 
 subprocess installed post-installation script returned error exit status 1

---

### Post by dcstar on 2010-08-16
> **omgwtf1337 said:**
> Slightly New user of Ubuntu 10.4

It doesn't seem to matter what i try and install or uninstall all lead to similar error messages. 
(TRYING TO INSTALL I GET)
.......
Errors were encountered while processing: 
** userful-multiplier **
Setting up userful-multiplier (341-20090901000926-0ubuntu1) ... 
Section "ubuntu 10.04" is not exist. 
(EE) Not supported linux system 
dpkg: error processing userful-multiplier (--configure): 
 subprocess installed post-installation script returned error exit status 1 
...........

I have no idea what that package is or what repository you added to get it, but manually uninstall it as it is **not** compatible with your system.

---

### Post by jringoot on 2010-09-13
I have the same issue: I try to get 2 keyboard/video/mouse  combinations to work on one computer. So that two users can share a computer at the same time. This software ([http://www2.userful.com/products/downloads/free-2-user](http://www2.userful.com/products/downloads/free-2-user)) claims to do it. And it is available in the Ubuntu repository.

I suppose it should be supported in Ubuntu as Canonical has a contract with them, see here: [http://www.canonical.com/news/ubuntu-10.04-for-software-vendors](http://www.canonical.com/news/ubuntu-10.04-for-software-vendors)



Alas: when trying to install it from the Ubuntu software center, the package doesn't recognise the ubuntu 10.04 distribution, and stops installation:

installArchives() failed: Preconfiguring packages ...

Preconfiguring packages ...

Selecting previously deselected package userful-multiplier.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 284032 files and directories currently installed.)

Unpacking userful-multiplier (from .../userful-multiplier_341-20090901000926-0ubuntu1_i386.deb) ...

Processing triggers for hal ...

Regenerating hal fdi cache ...

Processing triggers for python-gmenu ...

Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache...

Processing triggers for desktop-file-utils ...

Processing triggers for python-support ...

Setting up userful-multiplier (341-20090901000926-0ubuntu1) ...

Section "ubuntu 10.04" is not exist.

(EE) Not supported linux system

dpkg: error processing userful-multiplier (--configure):

 subprocess installed post-installation script returned error exit status 1

Setting up userful-multiplier (341-20090901000926-0ubuntu1) ...

Section "ubuntu 10.04" is not exist.

(EE) Not supported linux system

dpkg: error processing userful-multiplier (--configure):

 subprocess installed post-installation script returned error exit status 1

---

### Post by jringoot on 2010-09-13
and this is the output  I get from synaptic:
Setting up userful-multiplier (341-20090901000926-0ubuntu1) ...
Section "ubuntu 10.04" is not exist.
(EE) Not supported linux system
dpkg: error processing userful-multiplier (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 userful-multiplier
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up userful-multiplier (341-20090901000926-0ubuntu1) ...
Section "ubuntu 10.04" is not exist.
(EE) Not supported linux system
dpkg: error processing userful-multiplier (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 userful-multiplier

---

### Post by jringoot on 2010-09-13
Some more info on the package:

apt-cache showpkg userful-multiplier
Package: userful-multiplier
Versions: 
341-20090901000926-0ubuntu1 (/var/lib/apt/lists/mirror.ovh.net_ubuntu_dists_lucid_multiverse_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/mirror.ovh.net_ubuntu_dists_lucid_multiverse_binary-i386_Packages
                  MD5: f9925c889e297e303d8581c57d34dbe4


Reverse Depends: 
Dependencies: 
341-20090901000926-0ubuntu1 - python (2 2.4) libc6 (0 (null)) libexpat1 (0 (null)) libfreetype6 (0 (null)) libx11-6 (0 (null)) libgl1-mesa (16 (null)) libgl1 (0 (null)) zlib1g (0 (null)) libatk1.0-0 (0 (null)) libglib2.0-0 (0 (null)) libgtk2.0-0 (0 (null)) libpam0g (0 (null)) libpango1.0-0 (0 (null)) debconf (18 0.5) debconf-2.0 (0 (null)) desktop-multiplier (3 323-20090317110251) desktop-multiplier (3 323-20090317110251) 
Provides: 
341-20090901000926-0ubuntu1 - 
Reverse Provides:

---

### Post by jringoot on 2010-09-13
Whent the error occured in Synaptic, it gave me the option to file a bugreport.
Which I did: [https://bugs.launchpad.net/ubuntu/+source/userful-multiplier/+bug/637009](https://bugs.launchpad.net/ubuntu/+source/userful-multiplier/+bug/637009)

---

