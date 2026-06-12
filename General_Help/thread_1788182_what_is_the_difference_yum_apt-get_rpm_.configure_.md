---
title: "what is the difference yum apt-get rpm ./configure make install"
date: 2011-06-22
forum: General Help
---

### Post by raj17 on 2011-06-22
Hi,
I'm learning how to use linux. And i'm having many doubts. please answer them. I know this question might have been asked many times. and i've googled it also. But I could not find a satisfactory answer. Could  someone clearly explain me first of all what is yum, apt-get, rpm, ./configure  make install. how they r used. what is the difference between. which tool is used where and for what. I just know they r used to install softwares. r these tools? do all these come by default with every linux flavour.

---

### Post by wildmanne39 on 2011-06-22
> **raj17 said:**
> Hi,
I'm learning how to use linux. And i'm having many doubts. please answer them. I know this question might have been asked many times. and i've googled it also. But I could not find a satisfactory answer. Could  someone clearly explain me first of all what is yum, apt-get, rpm, ./configure  make install. how they r used. what is the difference between. which tool is used where and for what. I just know they r used to install softwares. r these tools? do all these come by default with every linux flavour.Hi, the one used by ubuntu is apt-get, yum and rpm is by other linux operating systems, they all do the same thing install software, the ./configure  make install is used by all linux operating systems some programs have to be installed that way, but most in ubuntu can be installed with the software center.

---

### Post by varunendra on 2011-06-23
yum, yast, apt, rpm,... are different package managers for different linux distros. Some, but not all, can be used interchangeably on different distros to manage (quite basically- install/uninstall) software packages.

rpm (RedHat Package Manager) also refers to the package format (<package name>.rpm) that is managed by the rpm package manager.

apt is mostly used for debian based distros (which use "<package name>.deb" format packages), although its variant for .rpm packages also exists.

apt-get is the commandline which only works with those distros which have apt installed.

So technically - yum, yast, apt, rpm (the package manager) are just different 'tools' to do the same job (with same or different package types),
apt-get is an optional command for distros that use apt as their package manager.

Lastly, './configure' and 'make install' are commands common to all linux distros, and are used when the software is not packaged, and needs to be compiled before installation using installation scripts provided with that software.

---

