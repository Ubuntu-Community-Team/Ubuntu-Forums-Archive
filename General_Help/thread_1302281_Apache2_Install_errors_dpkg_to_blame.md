---
title: "Apache2 Install errors: dpkg to blame?"
date: 2009-10-26
forum: General Help
---

### Post by psychoteddy on 2009-10-26
Hey guys, first post here.  I'm using 9.10 Karmic RC 64-bit and am unable to install apache2 on the system.  I have verified (with one of my friends) that I have the correct repositories, etc, but am still receiving the error.  

I have run apt-get update and apt-get upgrade to no avail.  Here is the error:

```
psychoteddy@MESSIAH-LINUX:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtagc0 php4-common libzzip-0-12
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2.2-bin apache2.2-common
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom
The following packages will be REMOVED:
  apache2-common
The following NEW packages will be installed:
  apache2 apache2.2-bin apache2.2-common
The following packages will be upgraded:
  apache2-mpm-prefork
1 upgraded, 3 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B/1,687kB of archives.
After this operation, 2,273kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 135706 files and directories currently installed.)
Unpacking apache2.2-bin (from .../apache2.2-bin_2.2.12-1ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/apache2.2-bin_2.2.12-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/apache2/modules/mod_auth_digest.so', which is also in package apache2-common 0:2.0.55-4ubuntu2.8
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/apache2.2-bin_2.2.12-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Thanks guys!

---

### Post by psychoteddy on 2009-10-26
Nevermind.  Looks like the prefetch package that Apache was pulling from was broken.  I removed this package and re-installed just fine.

---

### Post by Giblet5 on 2009-10-26
Nevermind then.

---

