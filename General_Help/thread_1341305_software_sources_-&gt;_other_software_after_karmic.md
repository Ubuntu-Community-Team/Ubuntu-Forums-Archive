---
title: "software sources -&gt; other software after karmic upgrade"
date: 2009-11-29
forum: General Help
---

### Post by smapdi636 on 2009-11-29
I'm confused about many of the entries I have in this list since upgrading from jaunty to karmic.

**Many seem to be jaunty-specific** -- for example, "Unsupported updates" has:

```
URI: http://us.archive.ubuntu.com/ubuntu/
Distribution: **jaunty**-backports
Components: main restricted universe multiverse
```

Others read, "disabled on upgrade to karmic" which makes me think those entries should be removed or updated.

What should I do to get this list trimmed/updated to relevant entries?

---

### Post by plucky on 2009-11-29
> **smapdi636 said:**
> I'm confused about many of the entries I have in this list since upgrading from jaunty to karmic.

**Many seem to be jaunty-specific** -- for example, "Unsupported updates" has:

```
URI: http://us.archive.ubuntu.com/ubuntu/
Distribution: **jaunty**-backports
Components: main restricted universe multiverse
```

Others read, "disabled on upgrade to karmic" which makes me think those entries should be removed or updated.

What should I do to get this list trimmed/updated to relevant entries?


Open a terminal and post output of ```
cat /etc/apt/sources.list
```

---

### Post by audiomick on 2009-11-29
the medibuntu source ( among other?? ) gets disabled when you update. You have to re-install it.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

A bit annoying, but I can accept it, given the reasons for medibuntu having to exist at all, and no great hassle really.

---

### Post by smapdi636 on 2009-11-29
> **plucky said:**
> Open a terminal and post output of ```
cat /etc/apt/sources.list
```

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.media.mit.edu/ubuntu/ karmic main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic universe
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner

deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-security multiverse

deb http://download.virtualbox.org/virtualbox/debian karmic non-free #virtualbox disabled on upgrade to karmic
deb http://wine.budgetdedicated.com/apt karmic main #wine disabled on upgrade to karmic
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main #ubuntu-tweak disabled on upgrade to karmic
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main #gnome-do disabled on upgrade to karmic
deb http://deb.opera.com/opera/ lenny non-free #opera disabled on upgrade to karmic
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu karmic main #openoffice disabled on upgrade to karmic
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main # disabled on upgrade to karmic
deb http://akirad.cinelerra.org akirad-jaunty main # disabled on upgrade to karmic
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main # disabled on upgrade to karmic
deb http://ppa.launchpad.net/keepassx/ppa/ubuntu karmic main # disabled on upgrade to karmic
deb http://ppa.launchpad.net/tarkus/ubuntu intrepid main # disabled on upgrade to karmic
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu karmic main
deb http://repos.zend.com/zend-server/deb server non-free
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```

---

### Post by plucky on 2009-11-29
Any line that does not have **karmic** in it needs to have a **#** put in front of it.Normally the upgrade process disables all the outside repositories.

So ```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb http://akirad.cinelerra.org akirad-jaunty main
deb http://ppa.launchpad.net/tarkus/ubuntu intrepid main
deb http://ppa.launchpad.net/tarkus/ubuntu intrepid main
```

all should have a **#** in front of them or be deleted during the upgrade.

Open a terminal and ```
gksudo gedit /etc/apt/sources.list
``` and add the # before the lines above,save, and then see what ```
sudo apt-get update
``` gives you


Good luck

---

### Post by smapdi636 on 2009-11-29
Thanks.  Working with the command line and text files vs. Synaptic made understanding this easier.

So I think I'm 99% straightened out at this point.  I have one lingering issue.

sudo apt-get update yields the error:

```
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com karmic-security/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-security/multiverse Sources
Fetched 3,399B in 1s (2,704B/s)
W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

**The string "openoffice" doesn't (anymore) even exist in sources.list...**

The only lines in /etc/apt/sources.list that have ppa.launchpad in them are:

```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/keepassx/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
```

---

### Post by fluffman86 on 2009-11-29
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

^^ remove that line.  Jaunty-backports are just some stuff that went into Karmic, so you already have that.

Your PPAs, etc, should work fine.

---

### Post by plucky on 2009-11-29
> deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) karmic main


That is in your sources.list and there isn't a karmic distribution on the server as I get a 404 code when I try to access it.Just put a # in front of it and see what "sudo apt-get update" gives you.

Good Luck

See [link](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/)

---

### Post by smapdi636 on 2009-11-29
This is what I'm confused about ... I can't find any reference to openoffice in my sources.list.  See greps below.

```

sudo apt-get update
...
...
...
Ign http://repos.zend.com server/non-free Packages
Hit http://repos.zend.com server/non-free Packages
Fetched 3,399B in 1s (1,820B/s)
W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
smap:/home/smap:**grep openoffice /etc/apt/sources.list**
smap:/home/smap:**grep ppa /etc/apt/sources.list**
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/keepassx/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
smap:/home/smap:
```

Also, for backports I changed the lines to:

```
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main universe multiverse restricted
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
```

Not sure if that's a waste or not but it's not throwing any errors.

---

### Post by plucky on 2009-11-30
> This is what I'm confused about ... I can't find any reference to openoffice in my sources.list.


It was in your original sources.list.
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.media.mit.edu/ubuntu/ karmic main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic universe
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner

deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-security multiverse

deb http://download.virtualbox.org/virtualbox/debian karmic non-free #virtualbox disabled on upgrade to karmic
deb http://wine.budgetdedicated.com/apt karmic main #wine disabled on upgrade to karmic
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main #ubuntu-tweak disabled on upgrade to karmic
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main #gnome-do disabled on upgrade to karmic
deb http://deb.opera.com/opera/ lenny non-free #opera disabled on upgrade to karmic
[color=red]deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu karmic main #openoffice disabled on upgrade to karmic[/color]
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main # disabled on upgrade to karmic
deb http://akirad.cinelerra.org akirad-jaunty main # disabled on upgrade to karmic
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main # disabled on upgrade to karmic
deb http://ppa.launchpad.net/keepassx/ppa/ubuntu karmic main # disabled on upgrade to karmic
deb http://ppa.launchpad.net/tarkus/ubuntu intrepid main # disabled on upgrade to karmic
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu karmic main
deb http://repos.zend.com/zend-server/deb server non-free
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```


Look at the whole list without using grep ```
cat /etc/apt/sources.list
```

Good Luck

---

### Post by smapdi636 on 2009-11-30
> **plucky said:**
> It was in your original sources.list.

It was but it is no longer and **sudo apt-get update** is **still throwing that error:**

```
Hit http://us.archive.ubuntu.com karmic-security/universe Sources
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com karmic-security/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-security/multiverse Sources
Fetched 3,399B in 1s (2,120B/s)
W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
```

Is there any other place besides sources.list that Ubuntu stores this type of information?  Here's my current /etc/apt/sources.list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main universe multiverse restricted

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse

deb http://download.virtualbox.org/virtualbox/debian karmic non-free
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
deb http://deb.opera.com/opera/ stable non-free
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/keepassx/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu karmic main
deb http://repos.zend.com/zend-server/deb server non-free
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```

---

### Post by plucky on 2009-11-30
> Is there any other place besides sources.list that Ubuntu stores this type of information?

```
cd /etc/apt/sources.list.d/
``` is where other lists might reside.

Good Luck

---

### Post by smapdi636 on 2009-11-30
> **plucky said:**
> ```
cd /etc/apt/sources.list.d/
``` is where other lists might reside.

Good Luck

**Bingo.**

Thanks!!

---

