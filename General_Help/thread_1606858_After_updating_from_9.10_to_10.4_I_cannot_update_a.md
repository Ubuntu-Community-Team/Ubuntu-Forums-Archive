---
title: "After updating from 9.10 to 10.4 I cannot update anything?"
date: 2010-10-27
forum: General Help
---

### Post by IIC0RRUPT10NII on 2010-10-27
Ok so I was using 9.10 because of my wifi not working in 10.4 (still does not but thats not the problem in this thread) well after getting my updates to update to 10.4 I run the package manager to update kernals and such, first it says theres an error failed to fetch CD then I reset my computer and it says my system is up to date but I do not have an option to upgrade to 10.10 and im sure theres updates my computer does not have..

---

### Post by plucky on 2010-10-27
> **IIC0RRUPT10NII said:**
> Ok so I was using 9.10 because of my wifi not working in 10.4 (still does not but thats not the problem in this thread) well after getting my updates to update to 10.4 I run the package manager to update kernals and such, first it says theres an error failed to fetch CD then I reset my computer and it says my system is up to date but I do not have an option to upgrade to 10.10 and im sure theres updates my computer does not have..

Post the output from a terminal of ```
lsb_release -a
cat /etc/apt/sources.list
```

---

### Post by IIC0RRUPT10NII on 2010-10-27
c0rrupt10n@iic0rrupt10nii-r00t:/etc/default$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid
c0rrupt10n@iic0rrupt10nii-r00t:/etc/default$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable disabled on upgrade to lucid

---

### Post by plucky on 2010-10-27
> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 10.04.1 LTS
Release: 10.04
Codename: lucid

Looks like you are up to date.

You could try ```
sudo apt-get dist-upgrade
``` to make sure you are up to date.

> but I do not have an option to upgrade to 10.10 

10.04.1 is a "Long Term Support" release,so it won't offer to upgrade to 10.10 until you go into "Software Sources" and change under the "Updates" tab,the Release Upgrade from LTS to Normal,and then reload.


> and im sure theres updates my computer does not have.. 

What makes you think this?

During an upgrade, the upgrade disables all non-canonical repositories,so if you had other repositories enabled,they would be disabled and the software that they contained would not be upgraded.

---

### Post by IIC0RRUPT10NII on 2010-10-27
AH! ok yes thank you I did not know that when updating from update manager installed all the updated kernals along with the updated distro.. ok that makes since as to why im up to date... also thank you for explaining the LTS update to me, now updating to 10.10

---

