---
title: "Help removing KDE &amp; kUbuntu software package(s)"
date: 2012-06-07
forum: General Help
---

### Post by ksaul on 2012-06-07
I was messing around with different Desktop environments and trying to upgrade to GNOME3.4 and somehow KDE got installed, and kdocs, and kterminal and whole bunch of other **** that comes with kUbunutu and I want to remove all this stuff... how is the safest/effective way to do it? 

HELP PLEASE!!!

---

### Post by 123456789123456789123456 on 2012-06-08
> **ksaul said:**
> I was messing around with different Desktop environments and trying to upgrade to GNOME3.4 and somehow KDE got installed, and kdocs, and kterminal and whole bunch of other **** that comes with kUbunutu and I want to remove all this stuff... how is the safest/effective way to do it? 

HELP PLEASE!!!

easiest way, go to terminal, run command
sudo apt-get install synaptic

synaptic package manager installs
search for every package you have installed for the kde environment, set these to be perminatly removed, make sure it did not disable any of the components needed for the original environment, if it did, click to enable them.
perform the marked activities, the manager should go ahead and remove the packages needed to be removed, and enable those packages that it was told to enable.
Restart of the computer would probably need to be done, as it will most likely keep using kde in ram until all the other packages can take back over.

---

### Post by mastablasta on 2012-06-08
> **123456789123456789123456 said:**
> search for every package you have installed for the kde environment, set these to be perminatly removed, make sure it did not disable any of the components needed for the original environment, if it did, click to enable them.
.
 
nice and what if the package is a dependency of another package?
 
to the OP do you have any KDE programme installed (such as k3b, kdenlive, Clementine or similar)? if so, then you probably need the kde packages to make it work. unless you have a pure gnome system.
 
kterminal? i know only konsole...
 
anyway how to get pure gnome: [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

