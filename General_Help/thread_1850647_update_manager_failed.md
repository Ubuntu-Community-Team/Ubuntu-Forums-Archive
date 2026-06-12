---
title: "update manager failed"
date: 2011-09-26
forum: General Help
---

### Post by Unguidedone on 2011-09-26
heyyyyyyyy :D


i have installed ubuntu to now 5 different computer systems and just love it but seems they all have a similar probelm:

the update manager fails

here are some archives

[http://ubuntuforums.org/archive/index.php/t-914025.html](http://ubuntuforums.org/archive/index.php/t-914025.html)

output of cat /etc/apt/sources.list  :

[HTML]julio@julio-ThinkCentre-M52:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
julio@julio-ThinkCentre-M52:~$ 
[/HTML]
what lines to i edit?

---

### Post by raja.genupula on 2011-09-26
Hi actually we need the output of 
```
sudo apt-get update
```.
please open your terminal and type the above command and paste the output what you got.

All the best.

---

### Post by Unguidedone on 2011-09-27
```
julio@julio-ThinkCentre-M52:~$ sudo apt-get update
[sudo] password for julio: 
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://us.archive.ubuntu.com maverick Release.gpg                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/techm3/outrec/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/techm3/outrec/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg        
Hit http://extras.ubuntu.com maverick Release                        
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://ppa.launchpad.net maverick/main Sources                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                    
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://us.archive.ubuntu.com maverick-updates Release            
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com maverick/main Sources               
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Ign http://ppa.launchpad.net maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Ign http://ppa.launchpad.net maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 72B in 2s (32B/s)
W: Failed to fetch http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
julio@julio-ThinkCentre-M52:~$ 

```

---

### Post by garvinrick4 on 2011-09-27
These below are all ppa's you have installed will show you a graphic. Open Software sources and remove check mark and then

sudo update-grub


Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages   404  Not Found 
Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found  W: 
Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
#They are most likely not valid anymore.

---

### Post by garvinrick4 on 2011-09-27
Here is a screenshot just click on it.  (they are kept in /etc/apt/sources.list.d  just for you info)

---

### Post by dFlyer on 2011-09-27
remove the following entries ppa from your apt source file.



Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

---

### Post by Unguidedone on 2011-09-27
seems that did the trick thanks for the help :D

now i got to do this for all the running systems i have eheheheh

(how do i mark as question or problem solved?)

---

### Post by garvinrick4 on 2011-09-27
Upper right of page under thread tools to mark as solved., Enjoy your Ubuntu.

---

