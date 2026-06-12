---
title: "Cannot update ubuntu 10.04 (Failed to fetch...malformed release file?)"
date: 2010-06-02
forum: General Help
---

### Post by Bad_Andy on 2010-06-02
Hi all, I am having a problem updating my Ubuntu (10.04 Lucid Lynx). I see that other have had this problem before back on Intrepid but I was unable to find any information about people having this problem recently so I thought I'd put a post up here looking for help.

When I try to update using Update Manager, I get the following errors:

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/Release  Unable to find expected entry  univers/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  Unable to find expected entry  univers/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  Unable to find expected entry  univers/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

the output of sudo apt-get update using terminal is thus:

```
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://archive.ubuntu.com lucid Release.gpg                     
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US   
Hit http://security.ubuntu.com lucid-security Release.gpg            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/univers Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                           
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/univers Translation-en_US
Hit http://archive.ubuntu.com lucid-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/univers Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Hit http://archive.ubuntu.com lucid-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://archive.ubuntu.com lucid Release    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://archive.ubuntu.com lucid-updates Release
Hit http://archive.ubuntu.com lucid-security Release
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/universe Sources
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/Release  Unable to find expected entry  univers/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  Unable to find expected entry  univers/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  Unable to find expected entry  univers/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

here is the content of my sources.list file:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main
deb-src http://archive.ubuntu.com/ubuntu lucid main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates univers main
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.ubuntu.com/ubuntu lucid-security main
deb-src http://archive.ubuntu.com/ubuntu lucid-security main
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid univers
deb http://security.ubuntu.com/ubuntu/ lucid-security univers main universe
```

any help is appreciated, thanks!

---

### Post by plucky on 2010-06-03
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid [color=red]univers[/color]
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security [color=red]univers[/color] main universe

Those repositories don't look right.

Edit the file ```
gksudo gedit /etc/apt/sources.list
```

and put a # at the beginning of both those lines.

Then run ```
sudo apt-get update
``` and see what happens.

Good Luck

---

### Post by type8code0 on 2010-08-22
I'm also have the same problem... after googled for sometimes, I have finally found the solution here

[http://jerwilkins.posterous.com/w-failed-to-fetch-httpusarchiveubuntucomubunt](http://jerwilkins.posterous.com/w-failed-to-fetch-httpusarchiveubuntucomubunt)

just edit 

> /etc/resolv.conf 

and put this at the top of it

> # google nameservers
nameserver 8.8.8.8
nameserver 8.8.4.4

> sudo apt-get update 

and no more error :)
hope it will help

---

### Post by the-kid on 2010-12-02
Thank you type8code0 your fix worked for me.

---

### Post by T0OL on 2011-07-09
> **the-kid said:**
> Thank you type8code0 your fix worked for me.
worked for me too

---

