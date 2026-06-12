---
title: "cannot upgrade or install programs"
date: 2009-12-25
forum: General Help
---

### Post by wwk2310 on 2009-12-25
Merry Christmas all.

I have been trying to repair this since I upgraded to 9.10 to no avail. Evidently something was corrupted on the upgrade.

I get the following errors which is typical:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdelibs4c2a texlive-base libyaml-syck-perl kdelibs-data texlive-common
  liblualib50 libyaml-perl texlive-base-bin libavahi-qt3-1 libdbus-qt-1-1c2
  texlive-font-utils liblua50 texlive-doc-base tex-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libucl1
The following NEW packages will be installed:
  libucl1 sbm
0 upgraded, 2 newly installed, 0 to remove and 305 not upgraded.
Need to get 426kB of archives.
After this operation, 1,561kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main libucl1 1.03-4 [27.7kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe sbm 3.7.1-9 [398kB]
Fetched 426kB in 4s (97.7kB/s)
Selecting previously deselected package libucl1.
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'busybox-initramfs' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

I have searched the forums and cannot find an answer.

Any hints appreciated.
Wendell

---

### Post by Leppie on 2009-12-25
have you tried adding a trailing new line to the file?
i think the concerning file is /var/lib/dpkg/info/busybox-initramfs.list

---

