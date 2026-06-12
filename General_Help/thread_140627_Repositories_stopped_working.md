---
title: "Repositories stopped working"
date: 2006-03-06
forum: General Help
---

### Post by HokeyFry on 2006-03-06
all of my online repositories in synaptic just stopped working. when i fire up synaptic i get errors for all online repos that they cant be statted. i can get occasional security updates but that is about it. in case something is screwed up with my sources.list, here it is:

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde35 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://apt.filefind.net/ breezy main contrib non-free

## created by arniemaxremoved
deb http://soulmachine.net/debian unstable/ 

```

if anyone can help, i would be very grateful.

---

### Post by Ramses de Norre on 2006-03-06
It's pretty hard to see what's wrong, try this repo's: [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")
And back up your old ones for sure ;)

---

### Post by noomz on 2006-03-06
Do u try 'sudo apt-get update' ?

(Dont have any idea now..it's my time to sleep but addict with ubuntu)

---

### Post by HokeyFry on 2006-03-06
thanks. apt-get update worked. synaptic works fine now.

---

### Post by stoeptegel on 2006-03-06
I got my sources.list updates with "source-o-matic", works great! :)
Check it out: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

