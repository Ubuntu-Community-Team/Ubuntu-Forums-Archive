---
title: "Size mismatch- python-dev"
date: 2006-02-21
forum: General Help
---

### Post by glave on 2006-02-21
I'm trying to install python-dev but apt-get is reporting a size mismatch.

I have tried doing --fix-missing without any luck, and I'm using the default repositories, so I'm a little lost as to what to try next.

```

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security maain restricted

```

---

### Post by kaamos on 2006-02-21
Can you remove and reinstall the package? Try also "sudo apt-get clean".

---

### Post by glave on 2006-02-21
Remove tells me that its not installed, I did clean and it executed ok, but I still get 
"Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4-dev_2.4.2-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4-dev_2.4.2-1_i386.deb)  Size mismatch"

---

