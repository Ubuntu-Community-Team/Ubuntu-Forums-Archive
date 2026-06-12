---
title: "Flash not installing on TWO Ubuntu based machines"
date: 2011-09-19
forum: General Help
---

### Post by computerkid2000 on 2011-09-19
Ok, earlier today, I was trying to install flash for firefox on a Ubuntu Server I set up (I put fluxbox also and use X over the network.) when I went through the process of firefox telling me to install missing plugins, it told me:

```
Flash Plugin NOT installed
```I thought it was not installing because it was missing a lot of X components of Normal Ubuntu.

Then after school (Yes, i do this at my school, no one seems to mind)
I had setup a Xubuntu computer in the ROTC building, some one told me that they could not install flash, I thought this was because of the limited account I setup, so i did things from my admin account, and did what I normally do and the same problem as with the server happened: Flash NOT installed

```
htf@ROTC1-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.40.0 libboost-date-time1.40.0 libgif4 gnash-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 137 not upgraded.
Need to get 2,120B/22.8kB of archives.
After this operation, 233kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse flashplugin-nonfree 10.3.183.7ubuntu0.10.04.1 [2,120B]
Fetched 2,120B in 0s (4,771B/s)               
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 96541 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.3.183.7ubuntu0.10.04.1_i386.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.3.183.7ubuntu0.10.04.1_i386.deb) ...
Setting up flashplugin-installer (10.3.183.7ubuntu0.10.04.1) ...
Downloading...
--2011-09-19 17:48:00--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.183.7.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 239 [text/html]
Saving to: `./adobe-flashplugin_10.3.183.7.orig.tar.gz'

     0K                                                       100% 21.6M=0s

2011-09-19 17:48:01 (21.6 MB/s) - `./adobe-flashplugin_10.3.183.7.orig.tar.gz' saved [239/239]

Download done.
sha256sum mismatch adobe-flashplugin_10.3.183.7.orig.tar.gz
The Flash plugin is NOT installed.

Setting up flashplugin-nonfree (10.3.183.7ubuntu0.10.04.1) ...
```i have done it using the firefox plugin installer, Synaptic and apt-get and it is the same thing over and over! it happened on two linux computers ON THE SAME NETWORK!

I dont know why sha256 would mismatch like that. Can anyone help?:confused:

---

### Post by computerkid2000 on 2011-09-19
The post went under, so *bump*

EDIT: Forgot to mention, i am using LTS for both machines

---

### Post by dcstar on 2011-09-20
> **computerkid2000 said:**
> The post went under, so *bump*

EDIT: Forgot to mention, i am using LTS for both machines

Quite possibly the network you are using is modifying the file via some crappy anti-virus system.

---

### Post by staticd on 2011-09-20
Tried manually downloading the tar ball and installing?

---

