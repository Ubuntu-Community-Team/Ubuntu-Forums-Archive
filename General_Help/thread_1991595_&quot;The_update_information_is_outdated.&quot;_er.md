---
title: "&quot;The update information is outdated.&quot; error"
date: 2012-05-30
forum: General Help
---

### Post by bhishan on 2012-05-30
I use Ubuntu 12.04 64bit in a dell inspiron 1525. Its been a couple of days, I see a error/warning sign (a red triangle with exclamation sign in it) on the top bar. Clicking on it the message says, "The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and then selecting 'Check for updates' and check if some of the listed repositories fail." There is no network problem since internet works fine. When I check for updates, there are none for the last 9 days and I don't get any message saying any repository has failed. I there were updates available, I haven't got them for over a week now. Need help.

---

### Post by llamabr on 2012-05-30
post the output of:

```
ls /etc/apt/
```

and 

```
cat /etc/apt/sources.list
```

There's something in one of those that's outdated.

Note: if you ignore this problem, nothing bad will happen, except you'll occasionally be annoyed when you look up at see the little Triangle. 

[http://ubuntuforums.org/images/icons/icon4.gif](http://ubuntuforums.org/images/icons/icon4.gif)

---

### Post by bhishan on 2012-05-30
```
$ ls /etc/apt
apt.conf.d     sources.list    sources.list.save  trusted.gpg   trusted.gpg.d
preferences.d  sources.list.d  trustdb.gpg        trusted.gpg~

```

```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise universe
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

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
```

---

### Post by llamabr on 2012-05-30
Great.  That all looks fine.  What happens with a:

```
sudo apt-get update
```

---

### Post by bhishan on 2012-05-30
The error message disappeared .... lol. I don't get it, but I'm happy :). Hope I'll still get the updates.

---

### Post by raja.genupula on 2012-05-30
cool! now mark the thread as solved from thread tools . Thank you .

---

### Post by bhishan on 2012-05-30
Just want to wait a couple days just to be sure.

---

### Post by raja.genupula on 2012-05-30
oh its fine but , if issue raise again we can unmark it as solved from thread tools itself .

---

### Post by bhishan on 2012-06-28
It appeared again and disappeared again after i updated using the terminal.```
sudo apt-get update
```I don't know what it is, but the problem is still there.

---

### Post by Just call me Oldmate on 2012-06-30
After running ```
sudo apt-get update
``` everything went fine but these at the bottom


```
W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```is there a way to get rid of these?

---

### Post by jmfal on 2012-06-30
Go to the other software tab in the Update Center

and put a check in both boxes for that ppa
if you don't need that ppa remove it, or remove the checks in both boxes for that ppa.

---

### Post by tiggsy on 2012-12-15
Getting the same type of error:
```
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_GB.bz2  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/i18n/Translation-en_GB.bz2  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/binary-i386/Packages.gz  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
getdeb.net isn't listed in my Other software tab, so presumably is part of the regular repositories?

I browsed to getdeb.net and it's offline, but the cached copy is asking for donations...

How do I fix this?

---

### Post by Adrianb93 on 2013-01-20
I have Ubuntu 12.04 and im having the same problem, with the same getdeb.net repos, its not a really big issue i just want to be able to see and choose which updates to install using the update manager and be sure im not missing any.

---

### Post by gpsvn on 2013-03-23
I have the same problem after install TOR.

>  ls /etc/apt/
apt.conf.d     sources.list              sources.list.save  trusted.gpg~
auth.conf      sources.list.d            trustdb.gpg        trusted.gpg.d
preferences.d  sources.list.distUpgrade  trusted.gpg

> cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) quantal main
deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) quantal main 




---

### Post by idoisler on 2013-05-20
Similar problem 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 3B22AB97AF1CDFA9 Launchpad PPA for Ubuntu-X

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/precise/Release](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

