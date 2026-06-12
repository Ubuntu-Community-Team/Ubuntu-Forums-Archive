---
title: "Could not download all repository indexes"
date: 2006-02-17
forum: General Help
---

### Post by Michael%S on 2006-02-17
Hello. I'm pretty much a Linux newbie, but I'm very interested in becoming more of an advanced user, so no need to spare me technical details.
Over the last couple of days, whenever I try to get a package or update a list of packages or anything of the sort, I get a "Could not download all repository indexes" error or something similar to it. Last time I tried, I got the following:
```
http://il.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg: Bad header line
http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz: Bad header line
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz: Bad header line
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz: Bad header line
http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz: Bad header line
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz: Bad header line
http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz: Bad header line
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz: Bad header line

```
I think it all started after I first tried to use EasyUbuntu. At first EUb said I need to fix my packages or something for it to work, then later I started getting the kind of thing I wrote about above.
Any help in solving these issues would be appreciated.

---

### Post by jrib on 2006-02-17
It seems there was a power failure where security.ubuntu.com is hosted and it was down for a while yesterday.  Just do 'sudo apt-get update' and it should work now.

[edit]If it is still not working, post your /etc/apt/sources.list

---

### Post by Michael%S on 2006-02-17
[QUOTE=_jason]It seems there was a power failure where security.ubuntu.com is hosted and it was down for a while yesterday.  Just do 'sudo apt-get update' and it should work now.

[edit]If it is still not working, post your /etc/apt/sources.list[/QUOTE]
Looks like it works, thanks a bunch. I had an inkling it would be something simple like this. :rolleyes:

---

### Post by Michael%S on 2006-02-17
Oh, looks like a similar problem remains, in EasyUbuntu. What I get is this:
```
http://packages.freecontrib.org/ubuntu/plf/dists/breezy/main/binary-i386/Packages.gz: 404 Not Found
http://packages.freecontrib.org/ubuntu/plf/dists/breezy/restricted/binary-i386/Packages.gz: 404 Not Found
http://packages.freecontrib.org/ubuntu/plf/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found
http://packages.freecontrib.org/ubuntu/plf/dists/breezy/multiverse/binary-i386/Packages.gz: 404 Not Found

```
And my sources.list file:
```
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free 
deb http://wine.sourceforge.net/apt/ binary/
deb http://deb.opera.com/opera etch non-free
# The above lines were generated automatically by EasyUbuntu.
# The rest of your sources.list follows




## Uncomment the following two lines to fetch updated software from the network

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://il.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
 deb-src http://il.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://il.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://il.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse


```

---

### Post by Michael%S on 2006-02-17
Well, looks like I solved the problem myself, more or less. I did [this]("p://www.psychocats.net/linux/sources.php") to my sources file and everything looks fine now. I ended up installing most of the packages that EUb installs on my own before I got to that though (just read the python file and looked for them on Synaptics).

---

