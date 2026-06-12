---
title: "Synaptic doesn't show updates"
date: 2006-05-08
forum: General Help
---

### Post by jozmak on 2006-05-08
Hi,

I am running xubuntu and yesterday, I enabled multiverse in synaptic because I needed a package from the repository. Right after installing it, I disabled multiverse again; and since then synaptic and the updater doesn't show the upgrades. It lists the installed and the not installed but not the upgradable packages. So I cannot update my system anymore. All the repositories are enabled as before. I am puzzled. Does anyone have any clue what could be wrong?

Thanks,
J. Mak

---

### Post by Ramses de Norre on 2006-05-08
```
sudo apt-get update && sudo apt-get upgrade
``` Does that work/give errors?
Post your /etc/apt/sources.list if it doesn't.

---

### Post by jozmak on 2006-05-08
apt-get update works fine.

mak@xubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


This is the sources.list

# 
# deb cdrom:[Xubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060403)]/ dapper main restricted


deb cdrom:[Xubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060403)]/ dapper main restricted

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Ramses de Norre on 2006-05-08
```
# deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
```
You've commented out the whole repo.
Make it to ```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
##deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
```
Or just remove universe and multiverse and uncomment it again.

---

### Post by jozmak on 2006-05-08
Thanks. This was the problem.

J. Mak

---

