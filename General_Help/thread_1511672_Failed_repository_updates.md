---
title: "Failed repository updates"
date: 2010-06-17
forum: General Help
---

### Post by aum11 on 2010-06-17
Something has happened to my repositories,  and now every repository comes up with failed.


Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


I am sure it is something simply, but I cannot see what.

Have tried different servers but all with the same failed responses.

Thanks for Your help.

$ cat /etc/apt/sources.list
$ cat /etc/apt/sources.list
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main multiverse

###### Ubuntu Update Repos
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main multiverse

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

---

### Post by garvinrick4 on 2010-06-17
Internet down, no connection.

---

### Post by aum11 on 2010-06-17
There is no problem with the internet connection.....

Some problem with the repositories?  I can't see a problem....as You can see I have reduced them to a minimum and still not working...this has really got me foxed...it started a couple of days ago.

---

### Post by dalpets on 2010-06-17
I also have the exact same problem-for nearly 2 weeks now!.

---

### Post by aum11 on 2010-06-17
I have another Ubuntu partition accessing the same home partition and it continues to work perfectly...so it is just this Lucid partition that is failing.

Ideas please?

---

### Post by philinux on 2010-06-17
Mine is a vanilla install of lucid. Here's my sources.list. Partner has been enabled as have backports.

What's in your sources.list.d directory?

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by aum11 on 2010-06-17
Thanks, well i installed Your source list in my system and run synaptic again and got the same old story, and tried with main and Australian server..what is happening here?


Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

BTW, the directory is /etc/apt/sources.list, or do You mean what is in sources.list.d?

---

### Post by plucky on 2010-06-17
Have you played with any proxy settings,or installed anything that might have altered proxy settings.

Open **System > Preferences > Network Proxy** and see if there are any proxy settings.Mine is set to direct internet connection.

Good Luck

---

### Post by aum11 on 2010-06-17
mine is direct also.

---

### Post by howefield on 2010-06-17
> **aum11 said:**
> mine is direct also.

Follow the links in this thread.

[http://ubuntuforums.org/showthread.php?p=9462061](http://ubuntuforums.org/showthread.php?p=9462061)

---

### Post by philinux on 2010-06-17
Have you installed google chrome?

[http://ubuntuforums.org/showthread.php?t=1445908](http://ubuntuforums.org/showthread.php?t=1445908)

See last post.

It does look like a proxy type issue.

---

### Post by aum11 on 2010-06-17
well I removed Chromium and rebooted and the problem with the failed repositories is still there:

 Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/jeremy-visser/python-iview/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jeremy-visser/python-iview/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://mirror.internode.on.net/pub/ubuntu/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by aum11 on 2010-06-17
Some time later the repositories are ok again.

I have reinstalled Chromium to check that it was not the problem.  All is still fine after the reinstall.

What can I say except it is a mystery?

---

