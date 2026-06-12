---
title: "Constant Software Center Error"
date: 2010-09-07
forum: General Help
---

### Post by gast0r on 2010-09-07
When installing applications I get an error saying that the package has failed to install correctly, and get have an output similar to this (this was me installing 20000 Lightyears Through Space):

installArchives() failed: W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages) 
Selecting previously deselected package libportmidi0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 213152 files and directories currently installed.) 
Unpacking libportmidi0 (from .../libportmidi0_1%3a200-0ubuntu1_amd64.deb) ... 
Selecting previously deselected package libsdl-ttf2.0-0. 
Unpacking libsdl-ttf2.0-0 (from .../libsdl-ttf2.0-0_2.0.9-1build1_amd64.deb) ... 
Selecting previously deselected package python-pygame. 
Unpacking python-pygame (from .../python-pygame_1.9.1release-0ubuntu1_amd64.deb) ... 
Selecting previously deselected package lightyears. 
Unpacking lightyears (from .../lightyears_1.3a-5_all.deb) ... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache... 
Processing triggers for python-support ... 
Setting up hid-dkms (0.11.1) ... 
Loading new hid-0.11.1 DKMS files... 
 
Error! Cannot locate /usr/src/hid-0.11.1.dkms.tar.gz. 
File does not exist. 
dpkg: error processing hid-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libportmidi0 (1:200-0ubuntu1) ... 
 
Setting up libsdl-ttf2.0-0 (2.0.9-1build1) ... 
 
Setting up python-pygame (1.9.1release-0ubuntu1) ... 
 
Processing triggers for python-central ... 
Setting up lightyears (1.3a-5) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for menu ... 
Errors were encountered while processing: 
 hid-dkms 
Setting up hid-dkms (0.11.1) ... 
Loading new hid-0.11.1 DKMS files... 
 
Error! Cannot locate /usr/src/hid-0.11.1.dkms.tar.gz. 
File does not exist. 
dpkg: error processing hid-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 2 

Most of the time however, they do install.

---

### Post by andrewthomas on 2010-09-07
try

```
sudo apt-get install lightyears
```

---

### Post by gast0r on 2010-09-07
No, the point is that hid-dkms seems to be interfering with all my installations. This leads me to believe that the package is broken. It also mentions a duplicate source, which I can't seem to find.

---

### Post by andrewthomas on 2010-09-08
> **gast0r said:**
> No, the point is that hid-dkms seems to be interfering with all my installations. **This leads me to believe that the package is broken**. It also mentions a duplicate source, which I can't seem to find.
```
sudo apt-get update && sudo apt-get safe-upgrade
```If you want to try and fix the problem, then post the output of the above command

---

### Post by gast0r on 2010-09-08
ross@ross-laptop:~$ sudo apt-get update && sudo apt-get safe-upgrade
[sudo] password for ross: 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB    
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB    
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg [189B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_GB              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net/mactel-support/ubuntu/](http://ppa.launchpad.net/mactel-support/ubuntu/) intrepid/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                       
Ign [http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/](http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/](http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/mactel-support/ppa/ubuntu/](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/) lucid/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed Release.gpg                    
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_GB
Ign [http://ppa.launchpad.net/webupd8team/mintmenu/ubuntu/](http://ppa.launchpad.net/webupd8team/mintmenu/ubuntu/) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/wfg/0ad/ubuntu/](http://ppa.launchpad.net/wfg/0ad/ubuntu/) lucid/main Translation-en_GB      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg                              
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release                                 
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release [44.7kB]             
Get: 6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Get: 7 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://deb.playonlinux.com/](http://deb.playonlinux.com/) karmic/main Translation-en_GB                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports Release                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed Release                        
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [70.0kB]        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages                       
Get: 9 [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release [1,723B]                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources                      
Get: 10 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                           
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages [295kB]       
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Get: 12 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,060B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Get: 13 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [671B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]    
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [22.5kB]        
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]     
Get: 17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [33.1kB]
Get: 18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [7,589B]    
Get: 19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,876B] 
Get: 20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [573B]    
Get: 21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages [3,270B]
Get: 22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources [106kB]
Get: 23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources [1,292B]
Get: 24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages [114kB]
Get: 25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources [38.2kB]
Get: 26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages [3,652B]
Get: 27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources [1,508B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed/universe Packages
Fetched 844kB in 1s (628kB/s)                     
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
E: Invalid operation safe-upgrade
ross@ross-laptop:~$

---

### Post by gast0r on 2010-09-12
**Bump.**

---

### Post by coffeecat on 2010-09-12
I can see at least three potential problems in the output from sudo apt-get update.

1 You have several PPA and third party repositories enabled. These can be of variable quality and there may be some sort of conflict going on here. Short of disabling them all I'm not sure what to suggest. Together with a mix of Karmic and Lucid repos and also the backports repo you are asking for breakage.

2 You have the proposed repository enabled...

> **gast0r said:**
> 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-proposed/universe Packages

Unless you are an experienced user this is a very bad idea. See:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

> **Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.**3 There is this error message:

> **gast0r said:**
> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)

To be honest, and I mean this kindly, with that smorgasbord of repositories I'm surprised you haven't experienced worse problems. Anyway, first things first. **Disable** the proposed repository and then let's see if we can do something about number 3. Post the contents of /etc/apt/sources.list and we can see which archive.canonical line(s) need dealing with.

I'm logging off now - late here - but I'm sure someone will help you with sources.list.

---

### Post by gast0r on 2010-09-16
I've disabled proposed. I've got a feeling this is a problem I'm going to have for ages. Hopefully it's not going to interfere badly with the Maverick upgrade.

---

### Post by davidmohammed on 2010-09-16
> **gast0r said:**
> I've disabled proposed. I've got a feeling this is a problem I'm going to have for ages. Hopefully it's not going to interfere badly with the Maverick upgrade.

has the problem been fixed?

if not type in a terminal session

gedit /etc/apt/sources.list

copy and paste the contents here.  Basically, you've got two or more lines that are exactly the same.  Comment out one of the lines (add a # at the start of the duplicate line).  Then run

sudo apt-get update && sudo apt-get upgrade

this should fix your duplicate error.

---

### Post by gast0r on 2010-09-16
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) intrepid main

Well that's the contents of my source list. I don't quite understand what your asking. Do you mean you want me to search for the duplicate source and add '#' to the start of it? If thats the case, I can't see a duplicate...

---

### Post by coffeecat on 2010-09-17
> **gast0r said:**
> I've disabled proposed.

No, you haven't. See:

> **gast0r said:**
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe

.. near the bottom of sources.list. It's still uncommented.

> **gast0r said:**
> Do you mean you want me to search for the duplicate source and add '#'  to the start of it? If thats the case, I can't see a duplicate...     

I can:

> **gast0r said:**
> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
[COLOR=red]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner[/COLOR]
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
[COLOR=red]deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner[/COLOR]
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) intrepid main

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe

The second entry is missing the ubuntu subdirectory but I guess those two lines are what dpkg is complaining about. The forum code has only made the beginning and ends of those two lines red - it's omitted reddening the urls - but you'll be able to see which two lines I mean.

> **gast0r said:**
>  Hopefully it's not going to interfere badly with the Maverick upgrade.

:shock: #-oA fruit salad of extra repositories is a sure fire way of breaking an upgrade. See:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
> Using packages from repositories not controlled by  Ubuntu is not recommended as it can be a security risk and may break or  complicate your upgrade. If you have used EasyUbuntu or Automatix  (neither of which is recommended nor supported), you may have problems  upgrading to a newer version and may require a fresh install. If you  have installed software from other sources, the upgrade may go more  smoothly if you [remove this software]("https://help.ubuntu.com/community/CleanUpgrade") before attempting the upgrade. The references to EasyUbuntu and Automatix are obsolete. They are long gone and good riddance to Automatix too. They should have called it Autobreakix. But you do have a load of 3rd party repos. When the time comes, do a fresh install of Maverick. Trust me. You'll save yourself a lot of wailing and gnashing of teeth. :wink:

---

### Post by gast0r on 2010-09-17
Ahh right, I really should learn to pay more attention, thanks a lot.

> The references to EasyUbuntu and Automatix are obsolete. They are long  gone and good riddance to Automatix too. They should have called it  Autobreakix. But you do have a load of 3rd party repos. When the time  comes, do a fresh install of Maverick. Trust me. You'll save yourself a  lot of wailing and gnashing of teeth. :wink:

When the installer starts up, it disables all third party repositories, so is this really a worry? Once complete I could easily just uninstall any application thats not working/interfering. I'm probably just looking at this in a very immature way.

---

### Post by coffeecat on 2010-09-17
> **gast0r said:**
> When the installer starts up, it disables all third party repositories, so is this really a worry? Once complete I could easily just uninstall any application thats not working/interfering. I'm probably just looking at this in a very immature way.

I wouldn't say immature. You make a valid point. In theory all 3rd party repos should be disabled by the package manager when you upgrade and uninstalling interfering applications should help. Nevertheless, I've seen a few threads where upgrades have broken a system and where over-enthusiastic use of 3rd-party repos may have been the problem.

I think a good strategy would be to try a dist-upgrade but to be prepared for a full re-installation if things go horribly wrong. Obviously, backup all your personal data first. Before you do a dist-upgrade check whether the 3rd-party repos you want are ready for Maverick yet. For example, at the time of posting, Medibuntu has not yet created a Maverick repository. With previous releases they had release-specific repos ready during the testing cycle. I don't know why they are late this time around.

By the way, if you intend to do an upgrade to Maverick before it goes final, beware of Update Manager while it's still in Beta. Have a look here:

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

So clearly, you would want to do a dist-upgrade from the terminal.

Good luck! :)

---

### Post by gast0r on 2010-09-17
What do you reckon the chances are of the Maverick Upgrade fixing hid-dkms? Like, would it update it, or possibly replace the package? It's getting pretty annoying now, and I'm convinced it's effecting the computer in some way. And in general I don't like getting constant errors when updating:P

---

### Post by coffeecat on 2010-09-17
I haven't a clue what hid-dkms is - except that I assume it's something to do with installing kernel modules for human interface devices. Does that sound familiar?  The package hid-dkms is not in my Lucid Synaptic, so it's not in the official Ubuntu repositories. Which means - I guess - that it comes from one of your 3rd party repos. And since a dist-upgrade will, as you rightly put it, disable the 3rd party repos, it certainly won't get upgraded.

Probably. :wink:

What you need to do is go to Synaptic, find hid-dkms, highlight it and click on the properties button. That will tell you what repo it comes from. You could also try marking it for uninstallation and see what other packages would be taken out. While you have the package highlighted, read the package description in the pane below. That might tell you how important it is for you. My hid devices (keyboard and mouse) work just fine without any 3rd party repos. :p

---

### Post by gast0r on 2010-09-19
It's from the Mactel repos. "This driver supplements the Apple function key mapping with useful defaults". It basically allows me to use the extra funtion keys that Apple add to Macbook Pros like 'expose' or 'dashboard'. I've tried reinstalls which doesn't seem to be doing much.

---

### Post by coffeecat on 2010-09-19
> **gast0r said:**
> It's from the Mactel repos. "This driver supplements the Apple function key mapping with useful defaults". It basically allows me to use the extra funtion keys that Apple add to Macbook Pros like 'expose' or 'dashboard'. I've tried reinstalls which doesn't seem to be doing much.

I don't know whether this link is of any use to you:

[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

I was using a full-size (with numpad) Apple aluminium keyboard when I had my Ubuntu machine and Mac Mini connected to the same peripherals with a KVM switch. Now that the switch has died, I've gone back to a Logitech keyboard for the Ubuntu machine. When I was using the Apple keyboard, I didn't bother with more than just the basic Fn key functions so I didn't explore that link much at all. What did irritate me with the Apple keyboard is that most times when  I tried to use the backspace key I would miss and hit the eject key instead, and the cupholder would hit me in the shin. :rolleyes:

---

### Post by gast0r on 2010-09-19
I shouldn't have much problems with this. I don't plan on using an external keyboard any time soon. I'm really impressed with just how much Ubuntu seems to work with Apple stuff. 

Oh, and should I mark this as solved? The main point hasn't been fixed but other stuff has.

---

### Post by coffeecat on 2010-09-19
> **gast0r said:**
> Oh, and should I mark this as solved? The main point hasn't been fixed but other stuff has.

Only the OP can mark a thread as solved, so it's up to you. You use the thread tools drop down above the first post. Even if you mark it as solved, someone may wander in and add a comment - sometimes a year or more later! I'll keep this on my subscribe list in case you need to add anything.

Good luck!

---

