---
title: "Installation problem"
date: 2012-09-20
forum: General Help
---

### Post by AADAS on 2012-09-20
When i try to install a package i get this error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnustep : Depends: systempreferences.app but it is not going to be installed
           Depends: gworkspace.app but it is not going to be installed
           Depends: terminal.app but it is not going to be installed
           Depends: preview.app but it is not going to be installed or
                    price.app but it is not going to be installed
           Depends: zipper.app but it is not going to be installed
           Depends: textedit.app but it is not going to be installed
           Depends: charmap.app but it is not going to be installed
           Recommends: gnumail.app but it is not going to be installed
           Recommends: talksoup.app but it is not going to be installed
           Recommends: viewpdf.app but it is not going to be installed
           Recommends: wmaker but it is not going to be installed
           Recommends: gnustep-icons but it is not going to be installed
           Recommends: gnustep-examples but it is not going to be installed
 nepenthes:i386 : Depends: libadns1:i386 (>= 1.4) but it is not going to be installed
                  Depends: libc6:i386 (>= 2.8) but it is not going to be installed
                  Depends: libcap2:i386 (>= 2.10) but it is not going to be installed
                  Depends: libcurl3-gnutls:i386 (>= 7.16.2-1) but it is not going to be installed
                  Depends: libgcc1:i386 (>= 1:4.1.1) but it is not going to be installed
                  Depends: libmagic1:i386 but it is not going to be installed
                  Depends: libpcap0.8:i386 (>= 0.9.8) but it is not going to be installed
                  Depends: libpcre3:i386 (>= 8.10) but it is not going to be installed
                  Depends: libstdc++6:i386 (>= 4.6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
What to do?

---

### Post by mr.suchy on 2012-09-20
Do u try 
```
 apt-get -f install 
``` ?

---

### Post by jerrrys on 2012-09-20
apt-get -f install This command does the same thing as **Edit->Fix Broken Packages** in Synaptic. Do this if you get complaints about packages with "unmet dependences".

more here on apt-get

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by AADAS on 2012-09-20
```
root@ip-10-252-62-231:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 nepenthes:i386 : Depends: libadns1:i386 (>= 1.4) but it is not installed
                  Depends: libc6:i386 (>= 2.8) but it is not installed
                  Depends: libcap2:i386 (>= 2.10) but it is not installed
                  Depends: libcurl3-gnutls:i386 (>= 7.16.2-1) but it is not installed
                  Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                  Depends: libmagic1:i386 but it is not installed
                  Depends: libpcap0.8:i386 (>= 0.9.8) but it is not installed
                  Depends: libpcre3:i386 (>= 8.10) but it is not installed
                  Depends: libstdc++6:i386 (>= 4.6) but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```
And what now?

---

### Post by BrianBlaze on 2012-09-20
> **AADAS said:**
> ```
root@ip-10-252-62-231:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 nepenthes:i386 : Depends: libadns1:i386 (>= 1.4) but it is not installed
                  Depends: libc6:i386 (>= 2.8) but it is not installed
                  Depends: libcap2:i386 (>= 2.10) but it is not installed
                  Depends: libcurl3-gnutls:i386 (>= 7.16.2-1) but it is not installed
                  Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                  Depends: libmagic1:i386 but it is not installed
                  Depends: libpcap0.8:i386 (>= 0.9.8) but it is not installed
                  Depends: libpcre3:i386 (>= 8.10) but it is not installed
                  Depends: libstdc++6:i386 (>= 4.6) but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```And what now?


I would apt-get each dependency see what happens?

---

### Post by jerrrys on 2012-09-20
Do you have your "universal sources" enabled?

If you are not sure, please post the the output of:

gedit /etc/apt/sources.list

---

### Post by AADAS on 2012-09-20
Note, this file is written by cloud-init on first boot of an instance
## modifications made here will not survive a re-bundle.
## if you wish to make changes you can:
## a.) add 'apt_preserve_sources_list: true' to /etc/cloud/cloud.cfg
##     or do the same in user-data
## b.) add sources in /etc/apt/sources.list.d
## c.) make changes to template file /etc/cloud/templates/sources.list.tmpl
#

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise main
deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-updates main
deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise multiverse
# deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise multiverse
# deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-updates multiverse
# deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
# deb-src [http://us-west-2.ec2.archive.ubuntu.com/ubuntu/](http://us-west-2.ec2.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

---

### Post by jrog on 2012-09-20
These are my "go to" steps if I encounter dependency issues/broken packages, so you might try them.

First, try:

```
sudo dpkg --configure -a
sudo apt-get install -f
```If that still doesn't fix the issue, try clearing APT's cache, updating your repo data, and then running the above commands again, like so:

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get dist-upgrade
```If that doesn't fix it, then answering some of the other things requested of you in this thread may help. For example, can we see your /etc/apt/sources.list file? (EDIT: Sorry, posted at the same time that you posted sources.list above; will check it now, but still try the commands listed here.)

---

### Post by AADAS on 2012-09-20
ubuntu@ip-10-252-62-231:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 nepenthes:i386 : Depends: libadns1:i386 (>= 1.4) but it is not installed
                  Depends: libc6:i386 (>= 2.8) but it is not installed
                  Depends: libcap2:i386 (>= 2.10) but it is not installed
                  Depends: libcurl3-gnutls:i386 (>= 7.16.2-1) but it is not installed
                  Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                  Depends: libmagic1:i386 but it is not installed
                  Depends: libpcap0.8:i386 (>= 0.9.8) but it is not installed
                  Depends: libpcre3:i386 (>= 8.10) but it is not installed
                  Depends: libstdc++6:i386 (>= 4.6) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by jrog on 2012-09-20
> **AADAS said:**
> ubuntu@ip-10-252-62-231:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 nepenthes:i386 : Depends: libadns1:i386 (>= 1.4) but it is not installed
                  Depends: libc6:i386 (>= 2.8) but it is not installed
                  Depends: libcap2:i386 (>= 2.10) but it is not installed
                  Depends: libcurl3-gnutls:i386 (>= 7.16.2-1) but it is not installed
                  Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                  Depends: libmagic1:i386 but it is not installed
                  Depends: libpcap0.8:i386 (>= 0.9.8) but it is not installed
                  Depends: libpcre3:i386 (>= 8.10) but it is not installed
                  Depends: libstdc++6:i386 (>= 4.6) but it is not installed
E: Unmet dependencies. Try using -f.
You can safely skip that step, then. Try the rest.

---

### Post by AADAS on 2012-09-20
Again the same.

---

### Post by jrog on 2012-09-20
> **AADAS said:**
> Again the same.
Can you post the contents of /var/log/dist-upgrade/apt.log?

---

### Post by AADAS on 2012-09-20
There is no dist-upgrade in log.

---

### Post by jrog on 2012-09-20
> **AADAS said:**
> There is no dist-upgrade in log.
Odd... Do you not use "sudo apt-get dist-upgrade" when you upgrade your system? Try running "sudo apt-get update && sudo apt-get dist-upgrade" to see if it creates a dist-upgrade in log. It ought to.

---

### Post by AADAS on 2012-09-20
ubuntu@ip-10-252-62-231:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 nepenthes:i386 : Depends: libadns1:i386 (>= 1.4) but it is not installed
                  Depends: libc6:i386 (>= 2.8) but it is not installed
                  Depends: libcap2:i386 (>= 2.10) but it is not installed
                  Depends: libcurl3-gnutls:i386 (>= 7.16.2-1) but it is not installed
                  Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                  Depends: libmagic1:i386 but it is not installed
                  Depends: libpcap0.8:i386 (>= 0.9.8) but it is not installed
                  Depends: libpcre3:i386 (>= 8.10) but it is not installed
                  Depends: libstdc++6:i386 (>= 4.6) but it is not installed
E: Unmet dependencies. Try using -f.
 and no new folder.

---

### Post by jrog on 2012-09-20
> **AADAS said:**
> ubuntu@ip-10-252-62-231:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 nepenthes:i386 : Depends: libadns1:i386 (>= 1.4) but it is not installed
                  Depends: libc6:i386 (>= 2.8) but it is not installed
                  Depends: libcap2:i386 (>= 2.10) but it is not installed
                  Depends: libcurl3-gnutls:i386 (>= 7.16.2-1) but it is not installed
                  Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                  Depends: libmagic1:i386 but it is not installed
                  Depends: libpcap0.8:i386 (>= 0.9.8) but it is not installed
                  Depends: libpcre3:i386 (>= 8.10) but it is not installed
                  Depends: libstdc++6:i386 (>= 4.6) but it is not installed
E: Unmet dependencies. Try using -f.
 and no new folder.
Wait a minute... This nepenthes package, how did you try to install it? It doesn't exist in precise, as far as I can tell. Did you try to install a .deb file not from the repos? Or are you using a PPA of some kind?

---

### Post by AADAS on 2012-09-20
> **jrog said:**
> Did you try to install a .deb file not from the repos? Yes.

---

### Post by jrog on 2012-09-20
> **AADAS said:**
> Yes.
Okay, well, that's the source of your problem. You can't just install a .deb and expect the dependencies to be resolved for you; dpkg (the low-level tool for installing .deb files) doesn't do that. You either need to manually install the dependencies that the system is telling you are needed (which can be a somewhat involved process), or you need to clear out the packages that you tried manually installing. If you decide to do the latter, a first step may be to try:

```
dpkg --purge nepenthes
```Then try using apt-get to update and upgrade, e.g., sudo apt-get update && sudo apt-get dist-upgrade. Let us know what happens. (Based on your first post, you may also be having problems with gnustep, but we'll get to that after you try this out first.)

---

### Post by AADAS on 2012-09-20
dpkg: warning: there's no installed package matching nepenthes

It is nepenthes:i386 not nepenthes.

---

### Post by jrog on 2012-09-20
> **AADAS said:**
> dpkg: warning: there's no installed package matching nepenthes

It is nepenthes:i386 not nepenthes.
So did you try both or just nepenthes? Do "sudo dpkg --purge nepenthes:i386", then. (The prior command also should have had a "sudo" in front of it; sorry about that.)

---

### Post by AADAS on 2012-09-20
Now everything is fine.

---

### Post by jrog on 2012-09-20
> **AADAS said:**
> Now everything is fine.
Great; glad it worked. Can you please mark this thread as solved using the Thread Tools at the top of the page?

---

