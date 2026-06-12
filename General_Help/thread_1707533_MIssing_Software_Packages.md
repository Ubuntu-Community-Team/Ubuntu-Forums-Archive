---
title: "MIssing Software Packages"
date: 2011-03-15
forum: General Help
---

### Post by freddiespagheti on 2011-03-15
I'm missing a number of software packages in both synaptic and apt-get. I've checked my sources.list file and have all the repositories enabled but certain packages are still not found.

I'm currently running 10.04 and at the moment the one I'm looking for in particular is [netgen]("http://packages.ubuntu.com/source/lucid/netgen").

I tried to compile from source but failed because I didn't have togl which, incidentally, I also could not download through the repositories.

---

### Post by zvacet on 2011-03-15
Just to be sure type

```
cat /etc/apt/sources.list
```

and post output here.You can also try to switch server to main under** ubnutu software center<edit>repositories**.Let us know if that worked.

---

### Post by freddiespagheti on 2011-03-16
```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://archive.canonical.com/ lucid partner

```

I switched the server to main but still don't have the packages even after running 'apt-get update'.

I tried upgrading to 10.10 but got a possibly related error from Update Manager:
> Not All Updates Can Be Installed.
Run a partial upgrade, to install as many packages as possible.

---

### Post by zvacet on 2011-03-16
After you changed and updated your source list did you try to install package.It is universe repo and from your source list you have that repo open.I really don´t see reason why you can not install that package.

---

### Post by freddiespagheti on 2011-03-16
Yes, I have tried that. It is still not there.

---

### Post by lithopsian on 2011-03-16
There is no netgen in the Lucid repositories.  I have no idea why.  Maybe you can get it from [here]("https://launchpad.net/ubuntu/+source/netgen").

---

### Post by freddiespagheti on 2011-03-16
Then why is this [netgen package]("http://packages.ubuntu.com/source/lucid/netgen") listed under lucid?

---

### Post by lithopsian on 2011-03-16
Don't argue with me.  You wanted to download netgen and I'm telling you it isn't there.  I said I don't know why.  Get over it.  Maybe the build failed.  Maybe it will show up in a few days.  Or maybe not.

No togl in Lucid either, never has been, never will be.  Maybe you could find a backport.  I'm surprised it would be needed to build netgen.  Maybe that's why there is no netgen package in Lucid ;)

---

### Post by zvacet on 2011-03-17
I think you should follow **lithopsian** advice and downlod package from link he posted to you.

---

