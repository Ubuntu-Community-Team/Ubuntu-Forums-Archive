---
title: "Can not Install programs with Ubuntu 10.04"
date: 2010-05-24
forum: General Help
---

### Post by jonsaunders on 2010-05-24
Hello,

I'm brand-spanking new to Ubuntu and so far am greatly enjoying this magnificent OS. Though, after attempting to install Wine, I now this error when trying to install any program:

'E:Type 'main' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list, E:The list of sources could not be read.'

Here is the source list where I'm assuming the error is coming from:

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse



Can anyone give me a hand? It would greatly be appreciated.

---

### Post by bodhi.zazen on 2010-05-24
That file looks fine, what is in this file ?

/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list

---

### Post by jonsaunders on 2010-05-24
It contains:

main
ttp://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main


Looks like an h is missing, could the be the problem?

---

### Post by bodhi.zazen on 2010-05-24
> **jonsaunders said:**
> It contains:

main
ttp://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main


Looks like an h is missing, could the be the problem?

Try changing that line to a single line:

```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main
```

FYI Usually we just add these lines to /etc/apt/sources.list , keeps it all in one place.

Along those lines, do you know how to use the ppa system ? Import the keys ?

---

### Post by jonsaunders on 2010-05-24
I don't. I was fiddling around with it while trying to install wine, I believe, and that may have caused this mess. 

How do I edit the file, gedit will not allow me to make adjustments to the text, Open Office only opens it in a read-only format, and notepad is not installed on my system.

---

### Post by oldos2er on 2010-05-24
To give yourself temporary admin privileges to edit that file, run ```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
``` in a terminal.

---

### Post by bodhi.zazen on 2010-05-24
> **jonsaunders said:**
> I don't. I was fiddling around with it while trying to install wine, I believe, and that may have caused this mess. 

How do I edit the file, gedit will not allow me to make adjustments to the text, Open Office only opens it in a read-only format, and notepad is not installed on my system.

See this page :

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

At the very bottom of the page :

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine
```One last caution: Wine is not a drop in replacement for Windows , not all windows applications work with with wine, and debugging problems with wine requires fairly advanced knowledge of BOTH Windows and Linux.

See : [https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

---

### Post by jonsaunders on 2010-05-24
Hey, problem solved. Thank you! I'll get on the ball and learn about PPA to help make sure this problem does not happen again.

---

