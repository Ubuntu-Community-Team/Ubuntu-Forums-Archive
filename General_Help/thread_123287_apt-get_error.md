---
title: "apt-get error"
date: 2006-01-29
forum: General Help
---

### Post by grandfso on 2006-01-29
Hello, everytime I try to do something with any new package(install, uninstall) i am getting such error:

Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
E: Pakiet ubuntu-docs ma zosta&#263; przeinstalowany, ale nie mo&#380;na znale&#378;&#263; jego archiwum.

In english:
Reading list of packages... done
Building dependency tree.. done
E: Package ubuntu-docs is supposed to be reinstalled, but unable to find it's archive.

---

### Post by dcstar on 2006-01-29
[QUOTE=grandfso]Hello, everytime I try to do something with any new package(install, uninstall) i am getting such error:

Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
E: Pakiet ubuntu-docs ma zosta&#263; przeinstalowany, ale nie mo&#380;na znale&#378;&#263; jego archiwum.

In english:
Reading list of packages... done
Building dependency tree.. done
E: Package ubuntu-docs is supposed to be reinstalled, but unable to find it's archive.[/QUOTE]
Post your /etc/apt/sources.list file contents here.

---

### Post by grandfso on 2006-01-29
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


## Uncomment the following two lines to fetch updated software from the network 
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced 
## after the final release of the distribution. 
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe' 
## repository. 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb http://us.archive.ubuntu.com/ubuntu hoary universe 
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe 

deb http://security.ubuntu.com/ubuntu hoary-security main restricted 
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted 

deb http://security.ubuntu.com/ubuntu hoary-security universe 
deb-src http://security.ubuntu.com/ubuntu hoary-security universe 

deb http://archive.ubuntu.com/ubuntu hoary multiverse 
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse 

## Backports
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted 
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted 

#################### 
#dodane z ununtu.pl# 
################### 

#deb http://pl.archive.ubuntu.com/ubuntu hoary-updates main restricted multiverse universe 
#deb http://security.ubuntu.com/ubuntu hoary-security main restricted multiverse universe 
#deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse 
#deb http://www.janw.easynet.be/rox/ i386/ # Rox-session 
#deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted # Ubuntu Backports 
#deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted # Ubuntu Backporst Extra

```
Thats all

---

