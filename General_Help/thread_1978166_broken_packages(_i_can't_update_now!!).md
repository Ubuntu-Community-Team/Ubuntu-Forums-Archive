---
title: "broken packages( i can't update now!!)"
date: 2012-05-11
forum: General Help
---

### Post by micatske on 2012-05-11
When i open the updare software center,or the ubuntu software center,there's a problem>>>>
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_mozillateam_firefox-next_ubuntu_dists_precise_main_i18n_Translation-zh
E: &#26080;&#27861;&#35299;&#26512;&#25110;&#25171;&#24320;&#36719;&#20214;&#21253;&#21015;&#34920;&#25110;&#29366;&#24577;&#25991;&#20214;&#12290;
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages)


and even i had tried the sudo apt-get check/update
promblem is here ...really need help,thx.
this promblem is just occur in today,i didn't find it yesterday. And i did nothing today.Strange

---

### Post by tomatoe on 2012-05-11
Hello!

Open synaptic, go to to edit -> fix broken packages.

---

### Post by micatske on 2012-05-11
Big problem is there. When i open synaptic,there is an error occur.says> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_mozillateam_firefox-next_ubuntu_dists_precise_main_i18n_Translation-zh
E: &#26080;&#27861;&#35299;&#26512;&#25110;&#25171;&#24320;&#36719;&#20214;&#21253;&#21015;&#34920;&#25110;&#29366;&#24577;&#25991;&#20214;&#12290;
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages)


and there is only the close button.and click it,i quit synaptic...thought it only can be solved through terminal now.

---

### Post by wojox on 2012-05-11
Ctrl+Alt+T to open the terminal.
```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get update
```

---

### Post by micatske on 2012-05-12
thanks , i have used the code, it works. But after i update once, reboot..the problem is still

---

### Post by Rubi1200 on 2012-05-12
Open a terminal as before and post the output of the following command:

```
cat /etc/apt/sources.list
```

Thanks.

---

### Post by micatske on 2012-05-14
> **Rubi1200 said:**
> Open a terminal as before and post the output of the following command:

```
cat /etc/apt/sources.list
```Thanks.

sorry for late reply for your post,busy these days.
```
[# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb http://mirror.bit6.edu.cn/ubuntu/ oneiric main restricted universe multiverse
# deb http://mirror.bit6.edu.cn/ubuntu/ oneiric-security main restricted universe multiverse
# deb http://mirror.bit6.edu.cn/ubuntu/ oneiric-updates main restricted universe multiverse
# deb http://mirror.bit6.edu.cn/ubuntu/ oneiric-backports main restricted universe multiverse
# deb http://mirror.bit6.edu.cn/ubuntu/ oneiric-proposed main restricted universe multiverse
# deb-src http://mirror.bit6.edu.cn/ubuntu/ oneiric main restricted universe multiverse
# deb-src http://mirror.bit6.edu.cn/ubuntu/ oneiric-security main restricted universe multiverse
# deb-src http://mirror.bit6.edu.cn/ubuntu/ oneiric-updates main restricted universe multiverse
# deb-src http://mirror.bit6.edu.cn/ubuntu/ oneiric-backports main restricted universe multiverse
# deb-src http://mirror.bit6.edu.cn/ubuntu/ oneiric-proposed main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://ppa.launchpad.net precise Release
deb http://archive.ubuntu.com/ubuntu precise universe

deb http://security.ubuntu.com/ubuntu/ precise-security restricted main multiverse universe


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
## developers who want to ship their latest software.

```

---

