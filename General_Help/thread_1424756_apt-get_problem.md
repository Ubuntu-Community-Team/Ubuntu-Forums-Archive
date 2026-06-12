---
title: "apt-get problem"
date: 2010-03-08
forum: General Help
---

### Post by amms on 2010-03-08
Hi All


I have my CD of Ubuntu server 9.04 server Edition.

I get a strange error in all my ubuntu installations ( more than 5 ).

I already do a fresh install and I keep get this error:


W: GPG error: [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) jaunty Release: Unknown error executi         ng gpgv
W: You may want to run apt-get update to correct these problems


What possible this could be ?
Is any think that I can do ?. I already try to alter the sources list and it works but I want to solve the problem and stick with my sources.list as it was:
[I]
#
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release amd64 (20090421.1)]/ jaunty
main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release amd64 (20090421.1)]/ jaunty m
ain restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

[/I]Thanks in advance

---

### Post by skymera on 2010-03-08
Can you go to:

System > Administration > Software Sources

Choose a new server, and try again

---

### Post by amms on 2010-03-08
Hi,


My instalation is ubuntu 9.04 server, I don't install the graphical environment.

I already try another sources, and it work. But I prefer to understand the problem and solve it with the current sources.list .

This are productive machines.

Any help.

---

### Post by wojox on 2010-03-08
Try it again. Sometimes the archive server is busy or something:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Also try reposting your sources.list in # tags so it's easier to read please.

---

### Post by lidex on 2010-03-08
> **amms said:**
> Hi All


I have my CD of Ubuntu server 9.04 server Edition.

I get a strange error in all my ubuntu installations ( more than 5 ).

I already do a fresh install and I keep get this error:


W: GPG error: [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) jaunty Release: Unknown error executi         ng gpgv
W: You may want to run apt-get update to correct these problems


What possible this could be ?
Is any think that I can do ?. I already try to alter the sources list and it works but I want to solve the problem and stick with my sources.list as it was:

[/I]Thanks in advance

Give it a couple of days/hours/minutes - there is/was an archive update in progress.

---

### Post by wojox on 2010-03-08
I just tried your GPG error: and it opened right up.

---

### Post by amms on 2010-03-08
Hi Wojox

In  test system I upgrave my kernel version ( to 2.6.28-18-server ) with apt-get dist-upgrade.

Although I keep receiving the error :
[I]W: GPG error: [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) jaunty Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems
[/I]

Have you try the source list that I past to this forum and get no error?.

If yes. What is your version of ubuntu ( uname -a ? )

---

