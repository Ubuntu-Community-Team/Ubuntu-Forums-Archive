---
title: "Could not download all repository indexes"
date: 2011-06-25
forum: General Help
---

### Post by IC2002 on 2011-06-25
When I try to use update manager I type in my password and check for updates the following message comes up on screen.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Inside a box in the window is the following:
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

I have tried going through older posts and tred someof the solutions there but nothing seems to work.Can anyone help???

IC2002

---

### Post by jerrrys on 2011-06-25
try the usual sudo apt-get update and sudo apt-get upgrade

if that gives the same results, please post a list of your software sources

---

### Post by IC2002 on 2011-06-25
I tried your recommendations and they did not solve the probem. This is what appeared

iain@TOSHIBA-User:~$ sudo apt-get upgrade
sudo: unable to resolve host TOSHIBA-User
[sudo] password for iain:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
iain@TOSHIBA-User:~$ sudo at-get update
sudo: unable to resolve host TOSHIBA-User
sudo: at-get: command not found
iain@TOSHIBA-User:~$

How do I post a list of my software sources?

Iain

---

### Post by jerrrys on 2011-06-25
gksudo gedit /etc/apt/sources.list

---

### Post by IC2002 on 2011-06-29
Have just tried that one and nothing happens.

---

### Post by jerrrys on 2011-06-30
edit out

---

### Post by IC2002 on 2011-07-01
I have tried it different ways to see if I am typing the command properly and I keep getting the same answer.

iain@TOSHIBA-User:~$ 
iain@TOSHIBA-User:~$ gksudo gedit/etc/apt/sources.list
iain@TOSHIBA-User:~$ gksudo gedit/etc/apt/sources.list
iain@TOSHIBA-User:~$ sudo gedit /etc/apt/sources.list
sudo: unable to resolve host TOSHIBA-User
sudo: gedit: command not found
iain@TOSHIBA-User:~$ sudo getit /etc/apt/sources.list
sudo: unable to resolve host TOSHIBA-User
sudo: getit: command not found
iain@TOSHIBA-User:~$ sudo getit/etc/apt/sources.list
sudo: unable to resolve host TOSHIBA-User
sudo: getit/etc/apt/sources.list: command not found
iain@TOSHIBA-User:~$ sudo gedit /etc/apt/sources.list
sudo: unable to resolve host TOSHIBA-User
sudo: gedit: command not found
iain@TOSHIBA-User:~$ sudo getit etc/apt/sources.list
sudo: unable to resolve host TOSHIBA-User

---

### Post by dFlyer on 2011-07-01
some of your entries don't have a space between gedit and /etc/apt/soruces.list. Just copy and paste this command.

gksu gedit /etc/apt/sources.list

---

### Post by IC2002 on 2011-07-01
For some reason it will not let me paste into the terminal but it will let me copy from the terminal, so I have had to type the commands in. I have tried the following variations but still nothing comes up in Terminal

iain@TOSHIBA-User:~$ gksu gedit etc/apt/sources.list
iain@TOSHIBA-User:~$ gksu gedit/etc/apt/sources.list
iain@TOSHIBA-User:~$ gksu gedit /etc/apt/sources.list
iain@TOSHIBA-User:~$

---

### Post by sandman887 on 2011-07-01
you can paste into the terminal by SHIFT-INSERT. Or right-clicking, and then selecting paste.

---

### Post by IC2002 on 2011-07-01
Ihavetriedthat and I can now copy ad paste into the terminal. I am still getting the same result though. Nothing is happening. I have copied and pasted the results below.

iain@TOSHIBA-User:~$ gksu gedit /etc/apt/sources.list
iain@TOSHIBA-User:~$ gksu gedit /etc/apt/sources.list
iain@TOSHIBA-User:~$

---

### Post by jerrrys on 2011-07-01
are you running ubuntu?

---

### Post by IC2002 on 2011-07-01
YesI am running Ubuntu, But I don't know which version or how to find out?

---

### Post by jerrrys on 2011-07-01
open a terminal and enter

**lsb_release -a**

---

### Post by IC2002 on 2011-07-01
This is what has come up.


iain@TOSHIBA-User:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.2
Release:    8.04
Codename:    hardy
iain@TOSHIBA-User:~$

---

### Post by jerrrys on 2011-07-01
interesting

[https://lists.ubuntu.com/archives/ubuntu-announce/2011-April/000144.html](https://lists.ubuntu.com/archives/ubuntu-announce/2011-April/000144.html)

---

### Post by IC2002 on 2011-07-01
Well thanks. I will have a goat updating..........More to follow I am sure.

Thanks

Iain:P

---

### Post by IC2002 on 2011-07-01
It is now telling me no upgrades are available.......or am I in the wrong place?

iain@TOSHIBA-User:~$ sudo apt-get install update-manager-core
sudo: unable to resolve host TOSHIBA-User
[sudo] password for iain: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
update-manager-core set to manually installed.
The following packages were automatically installed and are no longer required:
  libtwolame0 libgsf-gnome-1-114 guile-1.6 libpth20 libgoffice-0-common libmono0 libxml-libxml-common-perl
  python-software-properties libgda3-common libosp5 mplayer-skins libxml-namespacesupport-perl cli-common libnm-util0
  libtagc0 libmp4v2-0 libdns35 libpt-1.10.10-plugins-alsa libggzmod4 libgdl-gnome-1-0 libsqlite0 libclutter-0.6-0
  mono-common libpcrecpp0 guile-1.6-libs libgoffice-0-6-common bluez-utils libxevie1 dhcdbd libenca0 bluez-audio
  libgtksourceview2.0-common libggi2 libgii1 libhtml-tableextract-perl libxml-libxml-perl unattended-upgrades libggz2
  at-spi libxml-sax-perl libao2 mono-jit libqthreads-12 libgii1-target-x libgda2-3 libgda3-3 gnokii-common libggzcore9
  xulrunner-1.9-gnome-support fuse-utils libisc32 libgda2-common libguile-ltdl-1 libgdl-1-0 libntfs-3g23 libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
iain@TOSHIBA-User:~$ sudo do-release-upgrade
sudo: unable to resolve host TOSHIBA-User
Checking for a new ubuntu release
No new release found


Iain

---

### Post by jerrrys on 2011-07-01
you can no longer access updates thru normal channels.  i believe that you must use the backports.  something i have not tried.

could you do a fresh install?

also, you are really suppose to update first.  but maybe the alternate install cd will let you install 10o4.

one last thing.  before starting you should have backup in place

---

### Post by IC2002 on 2011-07-01
Thanks. I will make sure I do Back everything up. Thanks for your help.


Iain

---

### Post by IC2002 on 2011-07-12
I have tried to download and install 11.04 and boot it from a USB but the computer won't let the boot up take place from the USB port. Is there any way to download the updated system directly? As in without having to update first and use a disc or USB stick?

---

