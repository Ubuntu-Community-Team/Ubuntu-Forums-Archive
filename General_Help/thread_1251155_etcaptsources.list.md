---
title: "/etc/apt/sources.list"
date: 2009-08-27
forum: General Help
---

### Post by Bobrm2 on 2009-08-27
Having problems with PulseAudio in version 9.04. During the attempt to "repair" internet streaming somehow I've lost the ability to use Snaptic package manager and the Add/Remove programs (others are also italicized).  On another thread Snkiz suggested I post my /etc/apt/sources.list.

  Your assistance is most appreciated. I have no idea if the problem lies within the "/sources.list but here it is.

"# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
## following line created error msg
##PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main


##""

Above error message post below.
hu 27 Aug 2009 07:37:36 AM CDT

E: Type 'PulseAudio' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Thank you for any help.

Bob

---

### Post by dearingj on 2009-08-27
I don't know why this would make any difference, but have you tried putting a space between the second # and the name PulseAudio? It looks like all the other lines which are supposed to be ignored have that.

---

### Post by dmonkey on 2009-08-27
Try deleting the line ##PulseAudio..., you don't need it anyway.

---

### Post by utnubuuser on 2009-08-27
Those line... ARe they supposed to be Intrepid, and not hardy?
This is how they appear in the guide"
> # PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
from [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by Bobrm2 on 2009-08-27
Thank you, I first inserted a space, rebooted, then just deleted the ##PulseAudio line(s) and rebooted, to no avail. I believe the following is important here. Let me know if it isn't. Mean time I will return to trying to see about Pulse/Audio and how to make it work. This is where the problems started maybe I can stumble upon the "Fix".

  "In 9.04 JJ and Applications the following programs are not available to me on the Panel:

     Applications
    Add/Remove

Under System/Administration
   Software sources

Following error occur when attempting to invoke Synaptic Package Manager:
   "The window "Synaptic" is not responding"

  The ability to upgrade or remove unwanted programs has been lost. Any assistance most welcomed.

Bob

---

### Post by NoaHall on 2009-08-27
They shouldn't be intrepid - they should be jaunty.

Open a terminal and put in "sudo apt-get update" and post what you get.

---

### Post by grizato on 2009-08-27
With that many areas, it looks like you may aswell get a clean istall!
Or replace your sources with another persons and sudo apt-get update

---

### Post by Bobrm2 on 2009-08-27
Just got through deleting the last two lines, because they contained Intrepid Ibex. WIll return  to /etc/apt/sources.list and correct the issue. The instructions at:
  [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
confused me, easily done, first seeming to say to continue to part C, in the Howto, then and if you were running 9.04 just of reboot. I went on to Part C and now will add:

 deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main

Will reply asap. 


bob@Bob:~$ sudo apt-get update
[sudo] password for bob: 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release.gpg                               
Ign [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Translation-en_US                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg [189B]         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [49.6kB]       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release [49.6kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Ign [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Packages                   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [87.4kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                  
Ign [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [160kB]
Hit [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Packages                             
Hit [http://mirror.noreply.org](http://mirror.noreply.org) jaunty/main Sources                              
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2589B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [23.7kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [623B]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [34.2kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2589B] 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [7109B]     
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [44.9kB]       
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [623B]   
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [54.0kB]  
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [14.9kB]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [6637B] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2117B]  
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages [8256B]     
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages [14B] 
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages [9629B] 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages [14B] 
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [1662B]  
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [588B]    
Fetched 611kB in 7s (85.9kB/s)                                                 
Reading package lists... Done
bob@Bob:~$

---

### Post by NoaHall on 2009-08-27
There, it works!

---

### Post by Bobrm2 on 2009-08-27
The change to jaunty and addition to the back of /etc/apt/source.list rebooting then apt-get update brought 404 errors with regard to:
  deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main
  deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main

A dead end and have removed the lines.

Still unable to use the GUI(s) Synapti Package and Add/Remove.

Bob

---

### Post by NoaHall on 2009-08-27
try sudo apt-get upgrade . That should work. And then do gksudo synaptic

---

### Post by Bobrm2 on 2009-08-27
> **NoaHall said:**
> try sudo apt-get upgrade . That should work. And then do gksudo synaptic

Thank you. The GUI(s) don't function, but I can work on that.
Appreciate all the help.

Bob

---

### Post by oldos2er on 2009-08-27
> **Bobrm2 said:**
> The change to jaunty and addition to the back of /etc/apt/source.list rebooting then apt-get update brought 404 errors with regard to:
  deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main
  deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main

A dead end and have removed the lines.

Still unable to use the GUI(s) Synapti Package and Add/Remove.

Bob

 There appear to be only hardy and intrepid repos at that URL; that's why jaunty won't work.

---

### Post by brookie on 2009-08-27
I had problems with synaptic package manager crashing occassionally on three machines running Intrepid Desktop and I fixed them by doing this:

sudo dpkg --configure -a
sudo apt-get install -f

I found this information here:
[https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto")

---

