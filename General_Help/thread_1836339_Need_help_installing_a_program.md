---
title: "Need help installing a program"
date: 2011-08-30
forum: General Help
---

### Post by Malvazar on 2011-08-30
I have at one point in time installed a virtual cd drive program called CDemu. Since then I have had to reload my OS for different reason and such. Now I'm trying to reinstall the program but am finding difficult to for unknown reasons. If someone could help me that would be awesome. I'm running on Ubuntu 10.04 and the program in called CDemu.

---

### Post by kyletstrand on 2011-08-30
What steps have you taken?

This thread will take you through a step by step process of installation. 

[http://ubuntuforums.org/showthread.php?t=938030](http://ubuntuforums.org/showthread.php?t=938030)

---

### Post by Enigmapond on 2011-08-30
You need to add the PPA. Open the terminal and do:

```
sudo add-apt-repository ppa:cdemu/ppa
sudo apt-get update && sudo apt-get install cdemu
```

Cheers!:P

---

### Post by Malvazar on 2011-08-30
well i can't seem to get it to install no matter what I do. I try adding the ppa and it won't work (may have an outdated ppa though but can't find an up-to-date one). Tried looking for install files there are none. Everything really.

---

### Post by Enigmapond on 2011-08-30
Well the ppa I listed is valid and current...I think you have the name of the package wrong. Take a look here [https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa) I think you need to install three things.

                cdemu-client                              

cdemu-daemon                              
                
                                                                                                    gcdemu

---

### Post by Malvazar on 2011-08-31
No matter what ppa I try I can't get it to install. The terminal says it can't find the package, synaptic refuses for unknown reasons (just says that it will not install it). I'm starting to get really frustrated with this........

---

### Post by Enigmapond on 2011-08-31
I don't know what you are doing but...I just followed my instructions above and changed the install to cdemu-client....it installed...no hassles and so did the other two. Please do:

```
cat /etc/apt/sources.list
```

and post the results here..in between the code tags.

---

### Post by Malvazar on 2011-08-31
# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security restricted multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
#‘deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main’
#‘deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main’
#‘deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main’
#‘deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main’
#‘deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main’
#‘deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main’
#'deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main'
#'deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main'
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main

---

### Post by Enigmapond on 2011-08-31
Well..as I thought...you don't have the repo....please follow the instruction above and try it again installing the 3 packages I just installed...also...you need to remove all those tor lines except for the last 2...have no idea why there are so many...I'm surprised it hasn't told you there were duplicates.

---

### Post by Malvazar on 2011-08-31
you know what I just give up..... I don't understand why my system refuses to any of these commands..... I copy the the codes into the terminal exactly and all I get in errors. Every package I try says there is no package at all. 

malvazar@malvazar-desktop:~$ sudo apt-get install cdemu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cdemu
malvazar@malvazar-desktop:~$ sudo apt-get install cdemu-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cdemu-client
malvazar@malvazar-desktop:~$ sudo apt-get install cdemu-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cdemu-daemon
malvazar@malvazar-desktop:~$ sudo apt-get install gcdemu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gcdemu

---

### Post by Malvazar on 2011-08-31
Okay now that I have calmed down a little and made myself some dinner lets see if I can get this working now. I've purged all of my earlier work and deleted the old ppa and started over from scratch now. I've followed your directions to the "T" here and its still not working for my for some reason. Here is what I've done so far:

                                                                                                    malvazar@malvazar-desktop:~$ sudo add-apt-repository ppa:cdemu/ppa
[sudo] password for malvazar: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv AFDF4CC6A4F32AA9395FAE8F423A2125D782A00F
gpg: requesting key D782A00F from hkp server keyserver.ubuntu.com
gpg: key D782A00F: "Launchpad PPA for CDEmu" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
malvazar@malvazar-desktop:~$ sudo apt-get update && sudo apt-get install cdemu
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US              
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US   
Hit [http://deb.torproject.org](http://deb.torproject.org) lucid Release.gpg                                
Ign [http://deb.torproject.org/torproject.org/](http://deb.torproject.org/torproject.org/) lucid/main Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://deb.torproject.org](http://deb.torproject.org) lucid Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) lucid/main Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Ign [http://deb.torproject.org](http://deb.torproject.org) lucid/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                          
Ign [http://ppa.launchpad.net/cdemu/ppa/ubuntu/](http://ppa.launchpad.net/cdemu/ppa/ubuntu/) lucid/main Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Ign [http://deb.torproject.org](http://deb.torproject.org) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://deb.torproject.org](http://deb.torproject.org) lucid/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [13.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [14B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Fetched 14.3kB in 1s (9,821B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cdemu
malvazar@malvazar-desktop:~$ sudo apt-get install cdemu-client 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cdemu-client
malvazar@malvazar-desktop:~$ sudo apt-get install cdemu-daemon 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cdemu-daemon
malvazar@malvazar-desktop:~$ sudo apt-get install gcdemu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gcdemu
malvazar@malvazar-desktop:~$

---

### Post by mcduck on 2011-08-31
The reason it's not working is that the PPA only provides packages for latest Ubuntu version (11.04) while you are running an older release (10.04).

You'll have to find some other source for cdemu packages.

---

### Post by Malvazar on 2011-08-31
Well thats just great........ >.>

---

### Post by jfed on 2011-08-31
Here, these two might help. I hope.

[http://ubuntuforums.org/showthread.php?t=69530](http://ubuntuforums.org/showthread.php?t=69530)


[http://bozo3k.free.fr/debian/cdemu/](http://bozo3k.free.fr/debian/cdemu/)

---

### Post by jfed on 2011-08-31
Oops lol

---

