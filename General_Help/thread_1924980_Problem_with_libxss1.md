---
title: "Problem with libxss1"
date: 2012-02-13
forum: General Help
---

### Post by hadi812 on 2012-02-13
hi dear members
I'm new in ubuntu
i can not install prorams in terminal of ubuntu
my problem is this

E: Package 'libxss1' has no installation candidate

or 

 skype : Depends: libxss1 but it is not installable
E: Unable to correct problems, you have held broken packages


how can i fix this libxss1 ??????
i use this
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

but i have that problem always and i can not install skype, pidgin, chrom, clam and .....
 
please plase help me :(

---

### Post by drmrgd on 2012-02-13
Odd.  That package is showing up OK for me.  Would you mind posting the output of your:

```
sudo apt-get update
```

attempt.  Would be good to see if there are any errors or oddities there.

---

### Post by hadi812 on 2012-02-13
> **drmrgd said:**
> Odd.  That package is showing up OK for me.  Would you mind posting the output of your:

```
sudo apt-get update
```attempt.  Would be good to see if there are any errors or oddities there.

thank you friend
but i try that and i have that problem yet 
 :)

---

### Post by hadi812 on 2012-02-13
and i have problem with google chromium
when i push install buttun i see this problem

The following packages have unmet dependencies:

chromium-browser: PreDepends: lzma but it is a virtual package
                  Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
                  Depends: libxss1 but it is not going to be installed
                  Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
                  Depends: libnss3-1d (>= 3.12.3) but it is not going to be installed

---

### Post by drmrgd on 2012-02-14
Would you mind posting the output of:

```
sudo apt-get update
```

as well as the output of:

```
 cat /etc/apt/sources.list
```

It might show us why you're not able to install packages that seem to be in the repository as far as I can tell.

---

### Post by hadi812 on 2012-02-14
> **drmrgd said:**
> Would you mind posting the output of:

```
sudo apt-get update
```as well as the output of:

```
 cat /etc/apt/sources.list
```It might show us why you're not able to install packages that seem to be in the repository as far as I can tell.


i got this 

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/ oneiric partner
deb-src http://archive.canonical.com/ oneiric partner

```

---

### Post by drmrgd on 2012-02-14
I'll tell you, you have me a bit stumped at the moment.  It does look like you have the appropriate repository in there where I'm seeing the [package libxss1]("http://packages.ubuntu.com/oneiric/libs/libxss1").   

You didn't post the output of 'sudo apt-get update', and assuming that the update is not giving you and errors saying that it can't connect to the repository, I can't see why you're getting the "no installation candidate" error.  Usually that error comes from a package that's not listed in any of your repositories in your software sources.  

You could try running:

```
sudo dpkg --configure -a
```

to see if there are broken packages that need fixed first, then run:

```
sudo apt-get update
```

followed by:

```
sudo apt-get install libxss1
```

---

### Post by hadi812 on 2012-02-18
i try those but i have a problem again

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxss1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libxss1' has no installation candidate

[/HTML]

---

### Post by AoDcw on 2012-04-16
Problem fixed ?

If not I had the same problem. I fixed it with : "sudo apt-get -f install" (without package name)

---

