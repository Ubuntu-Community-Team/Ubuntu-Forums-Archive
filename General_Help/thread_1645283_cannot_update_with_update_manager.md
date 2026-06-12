---
title: "cannot update with update manager"
date: 2010-12-14
forum: General Help
---

### Post by sidious1741 on 2010-12-14
when trying to use update manager i get a window saying

"The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details
libc6 libc6-dev"


i tried apt-get install -f
```
timothy@timothy-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hplip-cups mplayer-skins
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0B/3,928kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 232717 files and directories currently installed.)
Preparing to replace libc6 2.12.1-0ubuntu9 (using .../libc6_2.12.1-0ubuntu10_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libc6_2.12.1-0ubuntu10_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.12.1-0ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

i have no idea what to do. libc6 sounds familiar. i think i installed it for something but i dont know what is wrong. Thanks so much.

---

### Post by TeoBigusGeekus on 2010-12-14
When you run apt-get from terminal don't forget to close update manager, software center and synaptic package manager.

---

### Post by sidious1741 on 2010-12-14
i should have known that from "is locked by another process." i have encountered that error before. with update manager closed i get the following

```
timothy@timothy-laptop:~$ sudo apt-get install -f
[sudo] password for timothy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hplip-cups mplayer-skins
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0B/3,928kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 232717 files and directories currently installed.)
Preparing to replace libc6 2.12.1-0ubuntu9 (using .../libc6_2.12.1-0ubuntu10_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libc6_2.12.1-0ubuntu10_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.12.1-0ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by TeoBigusGeekus on 2010-12-14
[See post #8.]("https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/349469")

---

### Post by sidious1741 on 2010-12-14
thanks, but unfortunately, that didnt work either

---

### Post by sidious1741 on 2010-12-18
After a reboot and not having to close update-manager, -f install took care of it.

---

