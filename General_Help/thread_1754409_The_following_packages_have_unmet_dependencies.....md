---
title: "The following packages have unmet dependencies...."
date: 2011-05-10
forum: General Help
---

### Post by mahmoodn on 2011-05-10
When I want to install a package I get this error
```
mahmood@mpc:~$ sudo apt-get install codeanalyst
[sudo] password for mahmood: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
codeanalyst is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  codeanalyst: Depends: binutils (>= 2.20.51.20100908) but 2.20.1-3ubuntu7 is to be installed
               Depends: libelfg0 (>= 0.8.12) but it is not going to be installed
               Depends: libpopt0 (>= 1.16) but 1.15-1 is to be installed
               Depends: libqt3-mt (>= 3:3.3.8-b) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Also -f option has no effect
```
mahmood@mpc:~$ sudo apt-get -f install codeanalyst
Reading package lists... Done
Building dependency tree       
Reading state information... Done
codeanalyst is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  codeanalyst: Depends: binutils (>= 2.20.51.20100908) but 2.20.1-3ubuntu7 is to be installed
               Depends: libelfg0 (>= 0.8.12) but it is not going to be installed
               Depends: libpopt0 (>= 1.16) but 1.15-1 is to be installed
               Depends: libqt3-mt (>= 3:3.3.8-b) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```
Any way to fix that?

---

### Post by sj1410 on 2011-05-10
just try

```

apt-get -f install

```

---

### Post by mahmoodn on 2011-05-10
This is what I get:
```
mahmood@mpc:~$ sudo apt-get -f  install
[sudo] password for mahmood: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libelfg0 libqt3-mt libaudio2 libmng1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libaudio2 libelfg0 libmng1 libqt3-mt
Suggested packages:
  nas libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc
The following packages will be REMOVED:
  codeanalyst
The following NEW packages will be installed:
  libaudio2 libelfg0 libmng1 libqt3-mt
0 upgraded, 4 newly installed, 1 to remove and 108 not upgraded.
1 not fully installed or removed.
Need to get 3,894kB of archives.
After this operation, 9,236kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main libaudio2 1.9.2-3 [85.0kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/main libelfg0 0.8.13-1 [57.8kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/main libmng1 1.0.9-1ubuntu1 [228kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid/main libqt3-mt 3:3.3.8-b-6ubuntu2 [3,523kB]
Fetched 3,894kB in 14s (266kB/s)                                                       
(Reading database ... 95947 files and directories currently installed.)
Removing codeanalyst ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libaudio2.
(Reading database ... 95410 files and directories currently installed.)
Unpacking libaudio2 (from .../libaudio2_1.9.2-3_amd64.deb) ...
Selecting previously deselected package libelfg0.
Unpacking libelfg0 (from .../libelfg0_0.8.13-1_amd64.deb) ...
Selecting previously deselected package libmng1.
Unpacking libmng1 (from .../libmng1_1.0.9-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libqt3-mt.
Unpacking libqt3-mt (from .../libqt3-mt_3%3a3.3.8-b-6ubuntu2_amd64.deb) ...
Setting up libaudio2 (1.9.2-3) ...

Setting up libelfg0 (0.8.13-1) ...

Setting up libmng1 (1.0.9-1ubuntu1) ...

Setting up libqt3-mt (3:3.3.8-b-6ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

then
```
mahmood@mpc:~$ sudo apt-get install codeanalyst
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package codeanalyst is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package codeanalyst has no installation candidate
```

So.....

---

### Post by sj1410 on 2011-05-10
your dependency problem is resolved,


> 
mahmood@mpc:~$ sudo apt-get install codeanalyst
[sudo] password for mahmood: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
codeanalyst is already the newest version.


it says codeanalyst is already the newest version. its already installed,

---

### Post by mahmoodn on 2011-05-10
```
codeanalyst is already the newest version
```

sorry where did you find that?

```
mahmood@mpc:~$ sudo apt-get install codeanalyst
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Red"]Package codeanalyst is not available[/COLOR], but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package codeanalyst has no installation candidate
```

I am sure it isn't installed
```

mahmood@mpc:~$ sudo find / -name "codeanalyst"
mahmood@mpc:~$ which codeanalyst
mahmood@mpc:~$ 

```

---

### Post by sj1410 on 2011-05-10
please see your first post

---

### Post by sj1410 on 2011-05-10
download and install it using dpkg -i

32bit
[http://developer.amd.com/Downloads/codeanalyst-2_13_2_44-Ubuntu1010Desktop32bit-Public.deb](http://developer.amd.com/Downloads/codeanalyst-2_13_2_44-Ubuntu1010Desktop32bit-Public.deb)

64bit
[http://developer.amd.com/Downloads/codeanalyst-2_13_2_44-Ubuntu1010Desktop64bit-Public.deb](http://developer.amd.com/Downloads/codeanalyst-2_13_2_44-Ubuntu1010Desktop64bit-Public.deb)

---

### Post by mahmoodn on 2011-05-10
I am stuck...
I have downloaded the deb package ```
mahmood@mpc:codean$ sudo dpkg -i codeanalyst-2_13_2_44-Ubuntu1010Desktop64bit-Public.deb
Selecting previously deselected package codeanalyst.
(Reading database ... 95420 files and directories currently installed.)
Unpacking codeanalyst (from codeanalyst-2_13_2_44-Ubuntu1010Desktop64bit-Public.deb) ...
dpkg: dependency problems prevent configuration of codeanalyst:
 codeanalyst depends on binutils (>= 2.20.51.20100908); however:
  Version of binutils on system is 2.20.1-3ubuntu7.1.
 codeanalyst depends on libpopt0 (>= 1.16); however:
  Version of libpopt0 on system is 1.15-1.
 codeanalyst depends on libqt3-mt (>= 3:3.3.8-b); however:
  Package libqt3-mt is not installed.
dpkg: error processing codeanalyst (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 codeanalyst

```
Also I am not able to remove binutils or upgrade
```
mahmood@mpc:codean$ sudo apt-get remove --purge binutils
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  codeanalyst: Depends: binutils (>= 2.20.51.20100908) but it is not going to be installed
               Depends: binutils (< 2.20.51.20100909) but it is not going to be installed
               Depends: libpopt0 (>= 1.16) but 1.15-1 is to be installed
               Depends: libqt3-mt (>= 3:3.3.8-b) but it is not going to be installed
  debootstrap: Depends: binutils but it is not going to be installed
  dpkg-dev: Depends: binutils but it is not going to be installed
  gcc-3.4: Depends: binutils (>= 2.16.1-2ubuntu3) but it is not going to be installed
  gcc-4.1: Depends: binutils (>= 2.17cvs20070426) but it is not going to be installed
  gcc-4.4: Depends: binutils (>= 2.20) but it is not going to be installed
  kernel-package: Depends: binutils (>= 2.12) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


mahmood@mpc:codean$ sudo apt-get upgrade binutils                                    Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  codeanalyst: Depends: binutils (>= 2.20.51.20100908) but 2.20.1-3ubuntu7.1 is installed
               Depends: libpopt0 (>= 1.16) but 1.15-1 is installed
               Depends: libqt3-mt (>= 3:3.3.8-b) but it is not installed
E: Unmet dependencies. Try using -f.

```
Any idea about that?

---

