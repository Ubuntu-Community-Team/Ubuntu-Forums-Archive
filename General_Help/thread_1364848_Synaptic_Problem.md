---
title: "Synaptic Problem"
date: 2009-12-26
forum: General Help
---

### Post by RedSingularity on 2009-12-26
I am trying to install the flash plugin and i get an error.  

E: /var/cache/apt/archives/flashplugin-installer_10.0.42.34ubuntu0.9.04.1_amd64.deb: conflicting packages - not installing flashplugin-installer


Any ideas?

---

### Post by taurus on 2009-12-26
```
sudo apt-get clean
sudo apt-get update
```

---

### Post by RedSingularity on 2009-12-26
Still getting the same error.......

---

### Post by taurus on 2009-12-26
Are you trying to install flash from the repos?  What does your /etc/apt/sources.list look like?

---

### Post by RedSingularity on 2009-12-26
Yeah

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
```

---

### Post by taurus on 2009-12-26
Are you looking into installing the ubuntu-restricted-extras package?  That should install flash among other plugins.

---

### Post by RedSingularity on 2009-12-26
Didnt think of that.....let me try it out.

---

### Post by RedSingularity on 2009-12-26
I get the same error when trying to install that.  Everything works fine when i try it except for the flash-plugin.

---

### Post by taurus on 2009-12-26
Edit /etc/apt/sources.list and remove the # in front of the backports repo.  Then, add the Canonical's repo.

```
deb http://archive.canonical.com/ubuntu jaunty partner
```
Save it and then run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by RedSingularity on 2009-12-26
Bahhh same error.  I dont understand this.  I never had this problem before.

---

### Post by taurus on 2009-12-26
```
sudo apt-get purge flashplugin-installer
sudo apt-get update
```

---

### Post by RedSingularity on 2009-12-26
When i try an purge i get this

Package flashplugin-installer is not installed, so not removed

---

### Post by Leppie on 2009-12-26
could it be that the 32bit flash plugin has been installed (maybe as a dependency or something)?

---

