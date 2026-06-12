---
title: "An Error Occured"
date: 2011-02-25
forum: General Help
---

### Post by wiggly81 on 2011-02-25
ok so i have a broken package in synaptic that i cant remove
i have tried many times but i get the same error, so if i put the error here maybe someone can help me out with this one...

```
terry@Shooter-PC:~$ sudo apt-get remove pidgin-ppa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  pidgin-ppa
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 73.7kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 222710 files and directories currently installed.)
Removing pidgin-ppa ...
gpg: key "67265EB522BDD6B1C69E66ED7FB8BEE0A1F196A8" not found: eof
gpg: 67265EB522BDD6B1C69E66ED7FB8BEE0A1F196A8: delete key failed: eof
dpkg: error processing pidgin-ppa (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 pidgin-ppa
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i cant run update manager it trys to have me run a partial upgrade which does not help anything, i cant remove from broken packages list and i cant even reinstall the .deb, i know there is bound to be a simple answer and i may have over looked somthing

---

### Post by dino99 on 2011-02-25
Seriously you might check your brain dude :(

pidgin is an existing package, pidgin-ppa is an url, do you get it ?

open synaptic third parties repo tab, and uncheck/remove this pidgin-ppa

into a terminal:

sudo rm /var/cache/apt/archives/*

then update upgrade again

---

### Post by wiggly81 on 2011-02-25
i am aware that the ppa is an url "dude" however i have not got pidgin installed on my system, i was going to install it after i installed the ppa.deb provided by the ppa team, however somthing has gone wrong when trying to install the .deb and now i cant remove / reinstall etc.....

```
into a terminal:

sudo rm /var/cache/apt/archives/*

then update upgrade again
```
already tried that..

i have now fixed the problem by manually adding the urls to software source list 
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) maverick main

---

### Post by bill516 on 2011-02-25
Ouch, been there and struggled.  Sounds like your app needs a key apt cannot find.  Did you install from the repos initially?  I have less trouble if I do not wander off the apt/synaptic reservation.

For now let's see if we can use a larger hammer.

> apt-get -f purge pidgin-ppa

The -f switch means "fix broken".  Apt will try to work around the problem.  "Purge" will remove the application and any configuration files it created.

A still heavier hammer is --fix-broken but do not resort to that unless you must.  It can do damage.

This is long but somewhere in it is everything to need to know bout apt.  Go to [http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

Good luck!

---

### Post by dino99 on 2011-02-25
from [https://launchpad.net/~ferramroberto/+archive/pidgin](https://launchpad.net/~ferramroberto/+archive/pidgin)

copy/paste: ppa:ferramroberto/pidgin 
into the "add" repo of third parties tab of synaptic

that it, no need headache.

---

