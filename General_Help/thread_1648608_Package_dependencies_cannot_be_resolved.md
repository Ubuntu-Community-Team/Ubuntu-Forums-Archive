---
title: "Package dependencies cannot be resolved"
date: 2010-12-19
forum: General Help
---

### Post by kurt3rd on 2010-12-19
I had uninstalled some applications in the past and when trying to reinstall similar or the same applications again I get this error. 

So I was using Deluge and uninstalled transmission.  Well deluge started to redownload all downloaded torrents, over and over again.  It got annoying so I wanted to reinstall transmission.  Well I get this error saying this:

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.
transmission

I tried going into synaptic -> custom filters -> missing re***mends and there is the package transmission-gtk.  I try to select it to be installed and I get this error:

Could not mark all packages for installation

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

transmission-gtk:
 Depends: libappindicator1 (>=0.0.19) but it is not installable
  Depends: libdbus-glib-1-2 (>=0.88) but 0.84-1 is to be installed
  Depends: libgconf2-4 (>=2.31.1) but 2.28.1-0ubuntu1 is to be installed
 Depends: libgdk-pixbuf2.0-0 (>=2.21.6) but it is not installable
  Depends: libnotify1 (>=0.5.0) but 0.4.5-1ubuntu4 is to be installed
  Depends: libssl0.9.8 (>=0.9.8m-1) but 0.9.8k-7ubuntu8.5 is to be installed

So I checked my repositories.  I have a few more than the basic ones but they are all enabled.  So I'm at a loss of what to do next :)

here is the info on my repositories

```
kurt@21tara:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.***/***munity/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.***/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.***/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.***/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.***/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.***/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.***/ubuntu/ lucid universe
deb http://us.archive.ubuntu.***/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.***/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.***/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.***/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.***/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.***/ubuntu/ lucid-updates multiverse

## Un***ment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.***/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.***/ubuntu/ lucid-backports main restricted universe multiverse

## Un***ment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.***/ubuntu lucid partner
deb-src http://archive.canonical.***/ubuntu lucid partner

deb http://security.ubuntu.***/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.***/ubuntu lucid-security main restricted
deb http://security.ubuntu.***/ubuntu lucid-security universe
deb-src http://security.ubuntu.***/ubuntu lucid-security universe
deb http://security.ubuntu.***/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.***/ubuntu lucid-security multiverse
deb http://archive.canonical.***/ lucid partner
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
deb http://archive.getdeb.net/ubuntu maverick-getdeb apps
deb http://dl.google.***/linux/deb/ stable non-free main
deb http://gb.archive.ubuntu.***/ubuntu dapper-backports main restricted universe multiverse
kurt@21tara:~$ ls -l /etc/apt/sources.list.d
total 48
-rw-r--r-- 1 root root  47 2010-12-19 01:01 dropbox.list
-rw-r--r-- 1 root root  47 2010-12-19 01:01 dropbox.list.save
-rw-r--r-- 1 root root 176 2010-12-19 01:01 google-chrome.list
-rw-r--r-- 1 root root 176 2010-12-19 01:01 google-chrome.list.save
-rw-r--r-- 1 root root 180 2010-12-19 01:01 google-talkplugin.list
-rw-r--r-- 1 root root 180 2010-12-19 01:01 google-talkplugin.list.save
-rw-r--r-- 1 root root  63 2010-12-19 01:01 lucid-bleed-ppa-lucid.list
-rw-r--r-- 1 root root  63 2010-12-19 01:01 lucid-bleed-ppa-lucid.list.save
-rw-r--r-- 1 root root 160 2010-12-19 01:01 medibuntu.list
-rw-r--r-- 1 root root 160 2010-12-19 01:01 medibuntu.list.save
-rw-r--r-- 1 root root  63 2010-12-19 01:01 ubuntu-wine-ppa-lucid.list
-rw-r--r-- 1 root root  63 2010-12-19 01:01 ubuntu-wine-ppa-lucid.list.save
```


Thanks all in advance :)

---

### Post by Yellow Pasque on 2010-12-19
> deb [http://gb.archive.ubuntu.***/ubuntu](http://gb.archive.ubuntu.***/ubuntu) dapper-backports main restricted universe multiverse

dapper-backports? Really?

---

### Post by Yellow Pasque on 2010-12-19
I should be more helpful. I see transmission is available from getdeb.net and you have the maverick version of getdeb in your sources. This is probably what's causing your issue.  You should either remove getdeb from your sources or use the lucid repo. If you really need something from their maverick catalog, download it separately.

---

### Post by kurt3rd on 2010-12-19
> **Temüjin said:**
> dapper-backports? Really?

what's wrong with that?  I just went through the net one day looking for repositories to add just to see what kinda software was out there.  I don't know much of anything about that stuff.

So I did what you said and removed getdb from the repository but it still shows up in ubuntu software center.  So transmission still brings back an error.  Is there a way to get it out of software center completely?

---

