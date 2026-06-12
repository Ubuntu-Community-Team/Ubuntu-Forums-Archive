---
title: "Installation and desktop questions"
date: 2006-01-25
forum: General Help
---

### Post by Calranthe on 2006-01-25
I've just installed Ubuntu on a Intel SE7210TP1-E server, standard configuration hardware wise,  2.8ghz processor, 1gb memory and 160gb sata drive.
Decided to use the Gnome desktop.

This is my second try at an install, I got slightly annoyed and vaped the HD starting again.

System is going to be used to house a c++ mud and a Java mud. 24/7.

Needs:
Good firewall with ability to setup access ports graphical interface prefered ability to do nice things like 8000/tcp 8070/tcp to allow incoming players (im use to mandrake)
any suggestions?

Full C++ support
Full Java 5.0 support

(My frustration came last time from downloading the sun java enterprise edition and it telling me I didn't have certain files (files will be quoted on nest post once I get to that point again) although I tripple checked and lib's needed were installed. 

I'm looking at the base install with normal updates just finishing now, clean system basically.

This is all pretty new to me in mandrake all C++ came in with the dev tools on installation and for java all I did was download the java bin to my desktop (graphical root) shifted it to root dir then typed chmod 777 j2eee....bin
./j2eee...bin
(not getting at Ubuntu I much prefer it just from the install and first few mins im just saying where my knowledge comes from)

---

### Post by Calranthe on 2006-01-25
Error when trying to install java
file i downloaded
j2eesdk-1_4_02_2005Q2-linux.bin

When I try to execute it.
error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory.

Just verified I have libstdc++6 installed

---

### Post by Calranthe on 2006-01-25
please can someone give me some ideas
here is what happens when try to configure my mud on the new system.
:/home/pyros/eom3/src/configure# ./configure
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output... configure: error: C++ compiler cannot create executables
:/home/pyros/eom3/src/configure#

these are installed im confused

---

### Post by engla on 2006-01-25
Are you sure those are installed?

Try 'sudo apt-get install build-essential'

---

### Post by Calranthe on 2006-01-25
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  dpkg-dev g++ gcc make
Suggested packages:
  debian-keyring manpages-dev autoconf automake1.9 libtool flex bison gcc-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ gcc make
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/605kB of archives.
After unpacking 1798kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package gcc.
(Reading database ... 72792 files and directories currently installed.)
Unpacking gcc (from .../gcc_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../archives/make_3.80-9_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up gcc (4.0.1-3) ...

Setting up g++ (4.0.1-3) ...

Setting up make (3.80-9) ...

Setting up dpkg-dev (1.13.10ubuntu4) ...
Setting up build-essential (11.1) ...
:~$

---

### Post by Calranthe on 2006-01-25
now the mud works, im kinda still confused, I went through the installing of packages etc did I miss out activating them or something ?

---

### Post by engla on 2006-01-29
I'm not sure what you're after but this is one thing:

The build-essensial command installed the things that you needed for ./configuring and compiling your mud application, the gcc compiler and those things. Gcc is normally _not_ installed on a vanilla ubuntu install.

But what other things are you confused about? You seem to have a lot of different things you try to do (java etc), but I don't know much about that.

---

