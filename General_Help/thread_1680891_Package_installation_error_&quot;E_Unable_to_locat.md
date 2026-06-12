---
title: "Package installation error: &quot;E: Unable to locate package xxx&quot;"
date: 2011-02-03
forum: General Help
---

### Post by LanguidLegend on 2011-02-03
I am following this [_guide_]("http://flurdy.com/docs/eclipse/install.html") to installing eclipse via terminal command-line on Linux. So I've downloaded all the necessary files and I am trying to install the jdk (jdk-6u23-linux-x64.bin) using this command:
```
sudo apt-get install fakeroot java-package
```
however, I just keep getting this output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package java-package
```
However, this seems to be happening lately with all the packages I try to install..
I checked the Synaptic Package Manager and reloaded and rebooted the computer, but to no avail.

Does anyone know how to fix this?

---

### Post by LanguidLegend on 2011-02-03
Oh, and here's whats in my /etc/apt/sources.list file in case you need it.
```
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```

---

### Post by janpol on 2011-02-03
In 10.10, Eclipse is available via the Software Center.

Just open the Software Center and search for "eclipse", click on install, and thats it.

That guide is **_really old_** and I think that java-package doesn't exist anymore in the repositories. If you want to install sun's (now Oracle's) sdk, you have to enable the Partner repositories and then just search for it in the software center.

Regards!

---

### Post by LanguidLegend on 2011-02-03
> **janpol said:**
> 
That guide is **_really old_** and I think that java-package doesn't exist anymore in the repositories. If you want to install sun's (now Oracle's) sdk, you have to enable the Partner repositories and then just search for it in the software center.

Thanks!
How do I enable the Partner repositories (not sure what that means exactly)?

---

### Post by janpol on 2011-02-03
A repository is the place where you get packages from. The "Partners" repository is a place where Canonical's partners and vendors upload packages for Ubuntu. Enabling it means that you will be able to install packages from it (like sun's java sdk). 

In order to do this, open the Ubuntu Software Center and go to Edit > Software Sources, then go to "Other Software" and enable the Partner repository. Then, click "Close" and when asked, click "Reload" and wait till it finishes refreshing the package list.

After that, just search for the Sun Java sdk and install it ;)

---

### Post by LanguidLegend on 2011-02-03
Cool, thanks!
Umm, sorry to bother again but I seem to have landed myself in a bigger issue: [_Thread:Serious bootup issues_]("http://ubuntuforums.org/showthread.php?t=1680939")
Can you take a look??

---

