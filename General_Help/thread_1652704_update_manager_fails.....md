---
title: "update manager fails...."
date: 2010-12-25
forum: General Help
---

### Post by vagrantjoe on 2010-12-25
My update manager "Fails to download repository information"
My internet is working fine though.
What do I do?

---

### Post by karthick87 on 2010-12-25
Post the output of,
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by vagrantjoe on 2010-12-25
joseph@joseph-Inspiron-1525:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


second code gives no output...
joseph@joseph-Inspiron-1525:~$ sudo dpkg --configure -a
[sudo] password for joseph: 
joseph@joseph-Inspiron-1525:~$ sudo dpkg --configure -a
joseph@joseph-Inspiron-1525:~$ 



joseph@joseph-Inspiron-1525:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_IN
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/) maverick/main Translation-en_IN
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/user/ppa/ubuntu/](http://ppa.launchpad.net/user/ppa/ubuntu/) maverick/main Translation-en
Err [http://ppa.launchpad.net/user/ppa/ubuntu/](http://ppa.launchpad.net/user/ppa/ubuntu/) maverick/main Translation-en_IN
  Error reading from server - read (104: Connection reset by peer)
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Fetched 632B in 38s (16B/s)
W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Error reading from server - read (104: Connection reset by peer)

W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by karthick87 on 2010-12-25
Also post these output pls,
```
cat /etc/apt/sources.list
```
```
ls -l /etc/apt/sources.list.d
```

---

### Post by vagrantjoe on 2010-12-25
joseph@joseph-Inspiron-1525:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

_________________________________________________________________


joseph@joseph-Inspiron-1525:~$ ls -l /etc/apt/sources.list.d
total 20
-rw-r--r-- 1 root root  92 2010-12-24 03:15 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root  92 2010-12-23 23:12 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root 154 2010-12-24 03:15 ubuntu-tweak-testing-ppa-maverick.list
-rw-r--r-- 1 root root 154 2010-12-23 23:12 ubuntu-tweak-testing-ppa-maverick.list.save
-rw-r--r-- 1 root root 122 2010-12-24 03:15 user-ppa-maverick.list
joseph@joseph-Inspiron-1525:~$

---

### Post by karthick87 on 2010-12-25
Try changing your server to main server (system>administration>software sources) and then update.

---

### Post by vagrantjoe on 2010-12-25
there's nothing like software sources in system>administration... And FYI I'm using Maverick...

---

### Post by karthick87 on 2010-12-25
In the sources.list, remove the '#' from 
> # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partnerso that it will look like,
> deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
Goto Sytem>>Administration>>Synaptic Package Manager and then goto Settings>>Repositories..Change the download from to Main server and then run your update..

---

### Post by gmargo on 2010-12-25
Pay attention to the error messages.

Here's one of the failing paths:
> 
[http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)
This is the sign of a misconfigured entry.  There is no [http://ppa.launchpad.net/user/](http://ppa.launchpad.net/user/) directory so the path is invalid.

You should show the contents of all the *.list files under /etc/apt/sources.d/.  I'd bet the bad one is the "user-ppa-maverick.list" file.

---

### Post by karthick87 on 2010-12-25
gmargo is right,remove that PPA and then update..Goto Sytem>>Administration>>Synaptic Package Manager and then goto Settings>>Repositories>>Other software and remove that PPA and then update..

---

### Post by vagrantjoe on 2010-12-25
I went to Sytem>>Administration>>Synaptic Package Manager and then goto Settings>>Repositories>>Other software and unchecked 2 other software repositories. They are...

 
[http://ppa.launchpad.net/user/ppa/ubuntu](http://ppa.launchpad.net/user/ppa/ubuntu) maverick main
[http://ppa.launchpad.net/user/ppa/ubuntu](http://ppa.launchpad.net/user/ppa/ubuntu) maverick main (source code)

The error message no longer appears... But I'm curious... Why did I get error messages suddenly... For 3 weeks update manager was working fine... I was wondering if I changed some setting while exploring ubuntu...

And also me unchecking those two repositories, will it affect my updates in any way?

---

