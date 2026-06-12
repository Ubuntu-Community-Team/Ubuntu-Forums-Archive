---
title: "Automatix"
date: 2006-03-22
forum: General Help
---

### Post by Linkhiei on 2006-03-22
when i run this code: ```
sudo apt-get install xterm libglade2-0 libgnomecanvas2-0
``` to install automatix on kubuntu i get this: ```
logan@WOLFY:~$ sudo apt-get install xterm libglade2-0 libgnomecanvas2-0 Reading package lists... Done Building dependency tree... Done xterm is already the newest version. Package libgnomecanvas2-0 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source E: Package libgnomecanvas2-0 has no installation candidate logan@WOLFY:~$ 
``` anyone know any solutions? ](*,)

---

### Post by arnieboy on 2006-03-23
```
sudo gedit /etc/apt/sources.list
```
and make it look as follows:
> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

save and exit and do:
```
sudo apt-get update
```
now try following the installation instructions for automatix

---

