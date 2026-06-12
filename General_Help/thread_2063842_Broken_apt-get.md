---
title: "Broken apt-get"
date: 2012-09-27
forum: General Help
---

### Post by bluestring on 2012-09-27
Similar to this post [http://ubuntuforums.org/showthread.php?t=1889843](http://ubuntuforums.org/showthread.php?t=1889843) I have tried to install code blocks using the sudo dpkg -i *.dep command. Now I have the same problem as he does and I can't get it fixed. I tried to use sudo apt-get -f install and it doesn't work.
```

murlin@myhome:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libiceutil34 linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic
  python-utidylib libzeroc-ice34 python-feedparser libtidy-0.99-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  codeblocks codeblocks-contrib codeblocks-contrib-dbg codeblocks-dbg
  libwxsmithlib-dev libwxsmithlib0-dev
Suggested packages:
  libwxgtk2.8-dev wx-common
The following NEW packages will be installed:
  codeblocks-contrib libwxsmithlib-dev
The following packages will be upgraded:
  codeblocks codeblocks-contrib-dbg codeblocks-dbg libwxsmithlib0-dev
4 upgraded, 2 newly installed, 0 to remove and 39 not upgraded.
4 not fully installed or removed.
Need to get 0 B/89.5 MB of archives.
After this operation, 112 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 210525 files and directories currently installed.)
Unpacking codeblocks-contrib (from .../codeblocks-contrib_10.05-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/codeblocks-contrib_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxSmithContribItems/wxchart/wxchart-1.0/include/wx/axis.h', which is also in package codeblocks-contrib-common 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libwxsmithlib-dev (from .../libwxsmithlib-dev_10.05-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwxsmithlib-dev_10.05-2_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxsmith/contrib/include/wx/propgrid/advprops.h', which is also in package wxsmith-headers 10.05-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/codeblocks-contrib_10.05-2_amd64.deb
 /var/cache/apt/archives/libwxsmithlib-dev_10.05-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by HiImTye on 2012-09-27
> **bluestring said:**
> Unpacking codeblocks-contrib (from .../codeblocks-contrib_10.05-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/**codeblocks-contrib_10.05-2**_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxSmithContribItems/wxchart/wxchart-1.0/include/wx/axis.h', which is also in package **codeblocks-contrib-common 10.05-1**
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking libwxsmithlib-dev (from .../libwxsmithlib-dev_10.05-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/**libwxsmithlib-dev_10.05-2**_amd64.deb (--unpack):
 trying to overwrite '/usr/include/wxsmith/contrib/include/wx/propgrid/advprops.h', which is also in package **wxsmith-headers 10.05-1**
remove the old versions of these packages and your problem should be resolved

---

### Post by bluestring on 2012-09-28
How would you go on to remove the packages? I tried using sudo apt-get remove (package name) but that doesn't seem to work as it says the file is not found on the system.

---

### Post by HiImTye on 2012-09-28
I would install either aptitude or synaptic and search for the packages.
```
sudo apt-get install aptitude
sudo apt-get install synaptic
```
to search in Synaptic, click on the search box in the top right corner and type in the name of the package you are looking for. if one exists, it will populate. to do a similar search in aptitude, do the following:
```
aptitude search codeblocks~i wxsmith~i
```
that will search for any installed packages (~i) starting with either 'codeblocks' or 'wxsmith'

I hope this helps

---

### Post by bluestring on 2012-09-28
I can't get any of the two packages installed because it says that I have other packages with unmet dependencies. It says I should fix those first with -f before doing anything else.
```

murlin@myhome:~$ sudo apt-get install aptitudeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: libboost-iostreams1.46.1 (>= 1.46.1-1) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
            Depends: libept1.4.12 but it is not going to be installed
            Recommends: libparse-debianchangelog-perl but it is not going to be installed
 codeblocks : Depends: libcodeblocks0 (= 10.05-1) but 10.05-2 is to be installed
              Depends: codeblocks-common (= 10.05-1) but 10.05-2 is to be installed
              Recommends: codeblocks-contrib (= 10.05-1) but it is not going to be installed
 codeblocks-contrib-dbg : Depends: codeblocks-contrib (= 10.05-1) but it is not going to be installed
 libwxsmithlib0-dev : Depends: wxsmith-dev (= 10.05-1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

The same thing happens when I try to install synaptic.

---

### Post by dino99 on 2012-09-28
Please post the result of: cat /etc/apt/sources.list

[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

[https://launchpad.net/ubuntu/+source/codeblocks](https://launchpad.net/ubuntu/+source/codeblocks)

---

### Post by bluestring on 2012-09-28
```
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ precise restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main

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
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports restricted universe multiverse main
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports restricted universe multiverse main

deb http://security.ubuntu.com/ubuntu precise-security restricted main
deb-src http://security.ubuntu.com/ubuntu precise-security restricted main
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

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

```

---

### Post by bluestring on 2012-09-28
Ok, I solved it by using 
```
sudo dpkg --force-all -P codeblocks codeblocks-contrib-dbg libwxsmithlib0-dev3
```

---

