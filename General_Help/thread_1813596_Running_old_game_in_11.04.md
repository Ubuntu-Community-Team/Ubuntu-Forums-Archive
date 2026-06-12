---
title: "Running old game in 11.04"
date: 2011-07-28
forum: General Help
---

### Post by thejurm on 2011-07-28
Hi,

I'm trying to install Creatures: Docking Station (a 32-bit program) in my 64-bit Ubuntu installation. I've found out so far I need to install libgtk1.2 (sometimes it says libgtk-1.2 as well, very weird). Looking around for information I found out I needed these packages (which I have downloaded):

libglib1.2-dev_1.2.10-19build1_amd64.deb
libglib1.2ldbl_1.2.10-19build1_amd64.deb
libgtk1.2_1.2.10-18.1build2_amd64.deb
libgtk1.2-common_1.2.10-18_all.deb
libgtk1.2-dev_1.2.10-18.1build2_amd64.deb

First try installing these gave me the issue of missing dependencies:

libx11-dev
libxext-dev
libxi-dev

I installed these using sudo apt-get install and then tried to install of these again using sudo dpkg -i *.deb and come across this problem:

```

(Reading database ... 176435 files and directories currently installed.)
Preparing to replace libglib1.2-dev 1.2.10-19build1 (using libglib1.2-dev_1.2.10-19build1_amd64.deb) ...
Unpacking replacement libglib1.2-dev ...
Preparing to replace libglib1.2ldbl 1.2.10-19build1 (using libglib1.2ldbl_1.2.10-19build1_amd64.deb) ...
Unpacking replacement libglib1.2ldbl ...
Selecting previously deselected package libgtk1.2.
Unpacking libgtk1.2 (from libgtk1.2_1.2.10-18.1build2_amd64.deb) ...
Preparing to replace libgtk1.2-common 1.2.10-18 (using libgtk1.2-common_1.2.10-18_all.deb) ...
Unpacking replacement libgtk1.2-common ...
Selecting previously deselected package libgtk1.2-dev.
Unpacking libgtk1.2-dev (from libgtk1.2-dev_1.2.10-18.1build2_amd64.deb) ...
Setting up libglib1.2ldbl (1.2.10-19build1) ...
dpkg: dependency problems prevent configuration of libgtk1.2:
 libgtk1.2 depends on libgtk1.2-common (>= 1.2.10-18.1build2); however:
  Version of libgtk1.2-common on system is 1.2.10-18.
dpkg: error processing libgtk1.2 (--install):
 dependency problems - leaving unconfigured
Setting up libgtk1.2-common (1.2.10-18) ...
dpkg: dependency problems prevent configuration of libgtk1.2-dev:
 libgtk1.2-dev depends on libgtk1.2 (= 1.2.10-18.1build2); however:
  Package libgtk1.2 is not configured yet.
dpkg: error processing libgtk1.2-dev (--install):
 dependency problems - leaving unconfigured
Setting up libglib1.2-dev (1.2.10-19build1) ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libgtk1.2
 libgtk1.2-dev

```

I've also tried loading the i386 versions of the packages, and extracting the packages and manually moving the files to the /usr/lib32/ directory.

I'm not sure exactly where to go from here, a push in the right direction would be much appreciated :) Thanks!

---

