---
title: "Some repositories fail to download."
date: 2012-07-14
forum: General Help
---

### Post by Ken147 on 2012-07-14
So after I did a clean install of 12.04 when it came out I noticed that some repositories failed to download and I thougth that it was just because of the load on their servers. but it's still happening now, and now it's saying that some information is out of date and may affect my internet connection and stuff. here is a screenshot below. any ideas?

---

### Post by Cheesehead on 2012-07-14
Often it just means that mirror is down. Downtime due to load is rare, even during the rush of a new release. Downtime due to other causes (maintenance, spot outage, accidents, hardware failure, etc.) is more common.

If downtime on that mirror is commmon, notify the mirror admins in IRC at #ubuntu-mirrors. If it's a spot outage, don't bother - the mirror owner certainly already knows.

In the meantime, use a different mirror. In Software Center or Synaptic, select Settings and pick another mirror from the list.

However, as Old_Gray_Wolf points out below, you didn't really do a clean install of 12.04

---

### Post by Old_Grey_Wolf on 2012-07-14
You said you  installed 12.04 but those repositories are for 10.04. Paste the output of this command in this thread.
```
cat /etc/apt/sources.list
```

---

### Post by Ken147 on 2012-07-14
> **Old_Gray_Wolf said:**
> You said you  installed 12.04 but those repositories are for 10.04. Past the output of this command in this thread.
```
cat /etc/apt/sources.list
```

Yes I did do a clean install, I even formated my Ubuntu partition before i installed 12.04

here is the output:

```
ken@kens-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

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
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

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
deb http://www.sourceslist.eu/repo/ubuntu lucid main non-free
ken@kens-laptop:~$ 

```

---

### Post by Old_Grey_Wolf on 2012-07-14
Edit the sources.list file and remove the last line
"deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free"

---

### Post by Ken147 on 2012-07-14
Thanks Old_Gray_Wolf, all errors are gone!!!! :D

---

