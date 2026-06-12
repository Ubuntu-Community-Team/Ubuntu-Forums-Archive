---
title: "An error occured, please run Package Manger from the right click menu"
date: 2012-05-18
forum: General Help
---

### Post by CallMeRicky on 2012-05-18
I am running ubuntu 12.04 LTS Last night I was trying to configure the repostory manually by going to ubuntu software center and adding a deb source. I clicked add and pasted this 'deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps'
But later that night I tried to install a package named Pytube and I got this error. 'Could not initialize the package information An unresolvable problem occurred when initializing the package information. Please report this bug against the 'update-manager' package and include the following error message:''E:Encountered a section with no Package: header, E:Problem with MergeList/var/lib/apt/lists/www.bashterritory.com_pytube_releases_Packages,E:The package lists or status file could not be parsed or opened.' Now I can't install anything or open Ubuntu Software Center without it force closing on me. HELP!

---

### Post by CallMeRicky on 2012-05-18
...

---

### Post by traditionalist on 2012-05-18
Go to Ubuntu tweak and edit the source files. Be [COLOR=Red]EXTREMELY[/COLOR] careful. Disable or delete the packages that are causing trouble;


[[IMG]http://img21.imageshack.us/img21/1994/selection021.th.png[/IMG]]("http://img21.imageshack.us/i/selection021.png/")



[[IMG]http://img535.imageshack.us/img535/2289/selection020f.th.png[/IMG]]("http://img535.imageshack.us/i/selection020f.png/")

Adding invalid info to the sources blocks a lot of things.  If you don't have Ubuntu tweak you can do it in Update Manager;

[[IMG]http://img406.imageshack.us/img406/1524/selection022.th.png[/IMG]]("http://img406.imageshack.us/i/selection022.png/")

if that does not work, you have to do it manually.  You have to enter your password to edit software sources.

---

### Post by Rubi1200 on 2012-05-19
Hi and welcome to the forums CallMeRicky :)

Open a terminal with Ctrl+Alt+T and post the contents of the sources list:

```
cat /etc/apt/sources.list
```

Let's take a look before doing anything and then we can look at options to fix this.

Thanks.

---

### Post by fittzwing on 2012-07-02
I have the same issue.  I'm on a new install (less than 32 hours)  Here's my sources.list:

kevinf@PGI-CEO:~$ cat /etc/apt/sources.list
#deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/

#deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/multiverse/binary-i386/
#deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/universe/binary-i386/
#deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

