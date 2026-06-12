---
title: "Unable to update kernel"
date: 2012-01-24
forum: General Help
---

### Post by tejaskale on 2012-01-24
Hello

OS: Ubuntu 11.10

I am unable to update my kernel. This is the error message I get when I type in 'sudo apt-get upgrade'
```

tejas@tejas-kale:~$ sudo apt-get upgrade
[sudo] password for tejas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-3.0.0-15-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/36.5 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
(Reading database ... 247018 files and directories currently installed.)
Preparing to replace linux-image-3.0.0-15-generic 3.0.0-15.25 (using .../linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Thanks for your help.

---

### Post by zvacet on 2012-01-24
```
sudo dpkg --configure -a
```

---

### Post by tejaskale on 2012-01-24
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

Thanks for the reply zvacet. Here is the output:-

```

tejas@tejas-kale:~$ sudo dpkg --configure -a
[sudo] password for tejas: 
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db

```

---

### Post by MaxPayneFH on 2012-02-29
I have the same bug, I wonder if anyone found a fix for this :(

---

### Post by michal.grno on 2012-06-14
I have the same bug, but not caused by man-db. For me it's:
```
Errors were encountered while processing:
 linux-image-3.2.0-24-generic
 linux-image-3.2.0-25-generic
 linux-image-generic
 linux-generic
 initramfs-tools

```
I'm going to reinstall :(

---

