---
title: "Ubuntu Software Center Repository"
date: 2012-09-16
forum: General Help
---

### Post by evilpoptart on 2012-09-16
I apologize if this was asked before, a quick search didnt turn up any helpful results.  

I recently installed Xubuntu 12.04 x64 on my laptop and would like to disable the "for purchase" software in the Software Center.  Is there a way I can do this?  Below is my /etc/apt/sources.list file:

```
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted multiverse
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```Thanks in advance.

---

### Post by jerrrys on 2012-09-16
Hi [evilpoptart]("http://ubuntuforums.org/member.php?u=1732516"), welcome to the forum :)

The short answer is no, the long answer is [here]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/629500")

---

### Post by vasa1 on 2012-09-16
> **jerrrys said:**
> Hi [evilpoptart]("http://ubuntuforums.org/member.php?u=1732516"), welcome to the forum :)

The short answer is no, the long answer is [here]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/629500")

The long answer, in turn, links to [this]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/630731").

There's a way to scratch your own itch but it involves editing various files and, really, is it such an issue? If you want to know more, take a look at [Is it possible to remove the commercial programs section from the Software Center]("http://askubuntu.com/q/47997/25656")?

---

### Post by vasa1 on 2012-09-16
Why your motive isn't explicitly mentioned, I haven't looked into whether the advice given in the askubuntu.com QnA actually speeds up loading of the USC or minimizes the bandwidth by not downloading excluded categories or has any other benefits than cosmetic ones.

---

### Post by evilpoptart on 2012-09-17
Honestly I'm just a big fan of the Linux software should be free philosophy and don't want to look at something I'm not using.  No real reason other than that.

Thanks everyone for the info.

---

