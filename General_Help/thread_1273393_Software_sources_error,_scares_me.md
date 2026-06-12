---
title: "Software sources error, scares me"
date: 2009-09-23
forum: General Help
---

### Post by akber on 2009-09-23
GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch http://deb.torproject.org/torproject.org/dists/<jaunty>/main/binary-i386/Packages  404 Not Found [IP: 88.198.151.34 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Thats the error right there. Is this software source important, if yes, how do i fix this problem (I had the exclamation warning sign in my task bar), and if no would it be cool to just remove the source entirely?

---

### Post by sisco311 on 2009-09-23
Just add the GPG key.

Open a terminal (Applications -> Accessories -> Terminal)
and run:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

[community/Medibuntu]("community/Medibuntu")

---

### Post by akber on 2009-09-23
Thanks

Edit: I put the code in the terminal and ran it and a bunch of stuff installed, but when i ran the update manager the same error came out

---

### Post by akber on 2009-09-24
bump

---

### Post by zinouch on 2009-09-24
change the source of software

---

### Post by akber on 2009-09-24
How do i do that. First i would like to know the particular software that is being update by that repository, and then how i fix it.

---

### Post by MelDJ on 2009-09-25
for medibuntu, you must get the ppa for it. Get it here [https://launchpad.net/~medibuntu-maintainers/+archive/ppa]("https://launchpad.net/%7Emedibuntu-maintainers/+archive/ppa"). to add it follow this video  [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

for the second problem, it seems a 404 error has come out. either the server is down or the website is no longer available

---

### Post by plucky on 2009-09-25
> Failed to fetch http://deb.torproject.org/torproject.org/dists/<jaunty>/main/binary-i386/Packages 404 Not Found [IP: 88.198.151.34 80]

jaunty should not have the < > arrows around it.Post the terminal output of ```
cat /etc/apt/sources.list
```


The **torproject.org** website does exist. Click [Here](http://deb.torproject.org/torproject.org/dists/jaunty/main/)

Good Luck

---

### Post by akber on 2009-09-27
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <jaunty> main

---

### Post by akber on 2009-09-27
How do i get rid of those <>!

---

### Post by NoaHall on 2009-09-27
gksudo gedit /etc/apt/sources.list

Remove the <> Around jaunty.

---

### Post by akber on 2009-09-28
Thanks, that did it. Ill also do the Pubkey thing because that error still pops up, but the warning sign is gone now and my system is up to date.

---

