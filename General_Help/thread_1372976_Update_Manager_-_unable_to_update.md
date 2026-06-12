---
title: "Update Manager - unable to update"
date: 2010-01-05
forum: General Help
---

### Post by Aberdeen-linux on 2010-01-05
Hi,

I have been trying to update my system using update manager and I have the following problem:

Update manager tells me that I can install 199 updates however is unable to download them. In the description of changes box I get the following error: Failed to download the list of changes. Please check your Internet connection.

I have no problem connecting to the internet..

Any help/suggestions would be greatly appreciated!

Thanks :)

---

### Post by Aberdeen-linux on 2010-01-05
Also I tried running sudo apt-get update && sudo apt-get upgrade and got the following errors:

Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) intrepid Release.gpg                      
  Could not connect to apsy.gse.uni-magdeburg.de:80 (141.44.96.210), connection timed out
Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) intrepid/main Translation-en_GB           
  Unable to connect to apsy.gse.uni-magdeburg.de http:
Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) intrepid/non-free Translation-en_GB       
  Unable to connect to apsy.gse.uni-magdeburg.de http:
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
  Unable to connect to archive.canonical.com http:
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid Release.gpg                              
  Could not connect to ftp.de.debian.org:80 (141.76.2.4), connection timed out
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid/main Translation-en_GB                   
  Unable to connect to ftp.de.debian.org http:
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid/non-free Translation-en_GB               
  Unable to connect to ftp.de.debian.org http:
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid/contrib Translation-en_GB                
  Unable to connect to ftp.de.debian.org http:
Err [http://apt.tt-solutions.com](http://apt.tt-solutions.com) intrepid Release.gpg                           
  Could not connect to apt.tt-solutions.com:80 (82.238.156.189), connection timed out
Err [http://apt.tt-solutions.com](http://apt.tt-solutions.com) intrepid/main Translation-en_GB                
  Unable to connect to apt.tt-solutions.com http:

---

### Post by plucky on 2010-01-05
> **Aberdeen-linux said:**
> Hi,

I have been trying to update my system using update manager and I have the following problem:

Update manager tells me that I can install 199 updates however is unable to download them. In the description of changes box I get the following error: Failed to download the list of changes. Please check your Internet connection.

I have no problem connecting to the internet..

Any help/suggestions would be greatly appreciated!

Thanks :)

Post your sources.list.Open a terminal and post output of ```
cat/etc/apt/sources.list
```

What is this repository? ```
http://apsy.gse.uni-magdeburg.de/
```

---

### Post by Leppie on 2010-01-05
> **plucky said:**
> What is this repository? ```
http://apsy.gse.uni-magdeburg.de/
```
looks like a neuroscience repo

---

### Post by Aberdeen-linux on 2010-01-05
Here is the my sources.list:

 deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) intrepid main non-free contrib
deb [http://apsy.gse.uni-magdeburg.de/debian](http://apsy.gse.uni-magdeburg.de/debian) intrepid main non-free
deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) intrepid main


The : deb [http://apsy.gse.uni-magdeburg.de/debian](http://apsy.gse.uni-magdeburg.de/debian) intrepid main non-free is for FSL a neuroimaging software that I use.

Thanks!

---

### Post by plucky on 2010-01-05
```
deb http://apt.tt-solutions.com/ubuntu/ intrepid main
```

There is no intrepid repository for this site.

```
deb http://apsy.gse.uni-magdeburg.de/debian intrepid main non-free
```

I think this should be have an extra / as shown in red.
```
deb http://apsy.gse.uni-magdeburg.de/debian[color=red]/[/color] intrepid main non-free
```

You can edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of the lines to eliminate them as a source of the problem.

Also put a # in front of this line ```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
``` as you don't want it looking for the CDrom.


Good Luck

---

### Post by Aberdeen-linux on 2010-01-05
Thanks for the advice!!

I have changed my source list as you suggested and now get the following error when I run apt-get update:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Any ideas?

---

### Post by drs305 on 2010-01-05
> **Aberdeen-linux said:**
> Thanks for the advice!!

I have changed my source list as you suggested and now get the following error when I run apt-get update:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Any ideas?

Normally that is what you would expect as an error message if you don't start the command with "sudo".
```
sudo apt-get update
```

---

### Post by Aberdeen-linux on 2010-01-05
Yes, I forgot to add the sudo, however when I do I get the following long list of errors:

Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg                          
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg                  
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security Release.gpg                 
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/main Translation-en_GB      
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/universe Translation-en_GB  
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-security/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) intrepid Release.gpg                      
  Could not connect to apsy.gse.uni-magdeburg.de:80 (141.44.96.210), connection timed out
Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) intrepid/main Translation-en_GB           
  Unable to connect to apsy.gse.uni-magdeburg.de http:
Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) intrepid/non-free Translation-en_GB       
  Unable to connect to apsy.gse.uni-magdeburg.de http:
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
  Unable to connect to archive.canonical.com http:
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid Release.gpg                              
  Could not connect to ftp.de.debian.org:80 (141.76.2.4), connection timed out
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid/main Translation-en_GB
  Unable to connect to ftp.de.debian.org http:
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid/non-free Translation-en_GB
  Unable to connect to ftp.de.debian.org http:
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid/contrib Translation-en_GB
  Unable to connect to ftp.de.debian.org http:
Reading package lists... Done                    
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg](http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_GB.bz2](http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_GB.bz2)  Unable to connect to archive.canonical.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to gb.archive.ubuntu.com http:

W: Failed to fetch [http://ftp.de.debian.org/debian/dists/intrepid/Release.gpg](http://ftp.de.debian.org/debian/dists/intrepid/Release.gpg)  Could not connect to ftp.de.debian.org:80 (141.76.2.4), connection timed out

W: Failed to fetch [http://ftp.de.debian.org/debian/dists/intrepid/main/i18n/Translation-en_GB.bz2](http://ftp.de.debian.org/debian/dists/intrepid/main/i18n/Translation-en_GB.bz2)  Unable to connect to ftp.de.debian.org http:

W: Failed to fetch [http://ftp.de.debian.org/debian/dists/intrepid/non-free/i18n/Translation-en_GB.bz2](http://ftp.de.debian.org/debian/dists/intrepid/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to ftp.de.debian.org http:

W: Failed to fetch [http://ftp.de.debian.org/debian/dists/intrepid/contrib/i18n/Translation-en_GB.bz2](http://ftp.de.debian.org/debian/dists/intrepid/contrib/i18n/Translation-en_GB.bz2)  Unable to connect to ftp.de.debian.org http:

W: Failed to fetch [http://apsy.gse.uni-magdeburg.de/debian/dists/intrepid/Release.gpg](http://apsy.gse.uni-magdeburg.de/debian/dists/intrepid/Release.gpg)  Could not connect to apsy.gse.uni-magdeburg.de:80 (141.44.96.210), connection timed out

W: Failed to fetch [http://apsy.gse.uni-magdeburg.de/debian/dists/intrepid/main/i18n/Translation-en_GB.bz2](http://apsy.gse.uni-magdeburg.de/debian/dists/intrepid/main/i18n/Translation-en_GB.bz2)  Unable to connect to apsy.gse.uni-magdeburg.de http:

W: Failed to fetch [http://apsy.gse.uni-magdeburg.de/debian/dists/intrepid/non-free/i18n/Translation-en_GB.bz2](http://apsy.gse.uni-magdeburg.de/debian/dists/intrepid/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to apsy.gse.uni-magdeburg.de http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by adam814 on 2010-01-05
System > Administration > Software Sources > Download From: > Other > Select Best Server

---

### Post by Aberdeen-linux on 2010-01-05
> **adam814 said:**
> System > Administration > Software Sources > Download From: > Other > Select Best Server


I have tried the above but get an error message saying that no suitable download server can be found. Please check your internet connection..

Not sure where to go next?

---

### Post by adam814 on 2010-01-05
Hmm...short of having firewalled apt I don't really see what's going on here.  Is Intrepid still officially supported?  Can you ping gb.archive.ubuntu.com?

---

### Post by Aberdeen-linux on 2010-01-05
> **adam814 said:**
> Hmm...short of having firewalled apt I don't really see what's going on here.  Is Intrepid still officially supported?  Can you ping gb.archive.ubuntu.com?

Don't think apt is firewalled, I definitely didn't put one on it. I've tried pining gb.archive.ubuntu.com and nothing seems to be happening....

Not sure if intrepid is still supported.

---

### Post by plucky on 2010-01-05
> **Aberdeen-linux said:**
> I have tried the above but get an error message saying that no suitable download server can be found. Please check your internet connection..

Not sure where to go next?

Everything is saying you don't have an internet connection.

What is your internet setup? 
Wired or wireless? 
Are you connected through a modem/router or USB modem?
Are you behind a proxy server?
Is this a new ubuntu installation?
Have you ever been able to update previously?

from a terminal ```
ping -c 5 ubuntu.com
```

**Intrepid is supported until April 2010**

---

### Post by Aberdeen-linux on 2010-01-05
> **plucky said:**
> Everything is saying you don't have an internet connection.

What is your internet setup? 
Wired or wireless? 
Are you connected through a modem/router or USB modem?
Are you behind a proxy server?
Is this a new ubuntu installation?
Have you ever been able to update previously?

from a terminal ```
ping -c 5 ubuntu.com
```

Its a wired connection through the university it is not a proxy connection. This is not a new installation and was able to update just fine until a couple of months ago.

When I try your suggestion of pinging ubuntu.com i get the following:
 ubuntu.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

Have made sure that I have no proxy settings enabled..so at a complete loss.

---

### Post by adam814 on 2010-01-05
Hmm...It doesn't give you an error resolving ubuntu.com, but ICMP ping packets don't make it back. And you don't have trouble with general web browsing?

As a university student myself I'd tend to blame university firewalls for inexplicable network behavior.  Maybe the latest version of Icarus considers apt repositories file-sharing:P

Do you have access to a system outside the university network you could try tunnelling through?

---

### Post by plucky on 2010-01-05
> **Aberdeen-linux said:**
> Its a wired connection through the university it is not a proxy connection. This is not a new installation and was able to update just fine until a couple of months ago.

When I try your suggestion of pinging ubuntu.com i get the following:
 ubuntu.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

Have made sure that I have no proxy settings enabled..so at a complete loss.

Something is blocking pings as you are not receiving replies to the ping command.You need to check with your university network administrators as to what traffic is allowed and what they have blocked.

They probably restrict certain types of traffic so that the network doesn't get overwhelmed with all the students downloading from the internet.

Good Luck

---

### Post by Aberdeen-linux on 2010-01-05
> **adam814 said:**
> Hmm...It doesn't give you an error resolving ubuntu.com, but ICMP ping packets don't make it back. And you don't have trouble with general web browsing?

As a university student myself I'd tend to blame university firewalls for inexplicable network behavior.  Maybe the latest version of Icarus considers apt repositories file-sharing:P

Do you have access to a system outside the university network you could try tunnelling through?


Thanks again for all your help. Its really weird no problems browsing the internet and my wired connection says its connected just fine. Unfortunately I don't have access to a system outside the uni to try tunnelling with..So i'm really stuck at the moment :(

Any other suggestions?

---

### Post by jiggles100 on 2010-01-05
Hey there neighbour :)
 
Definitely something weird going on there.
 
Can you take one of the repository addresses and paste it into your browser?  It's all http stuff so you should at least see an index page with a list of folders.
 
e.g [http://gb.archive.ubuntu.com/](http://gb.archive.ubuntu.com/)
 
  That should confirm that the issue isn't a connection problem and your ping results aren't an ICMP block by the uni.
 
Are you trying to do the update at the same time of day?  Clutching at straws but it might be a peak time problem.  I'll try to pop past on the way home.

---

### Post by Aberdeen-linux on 2010-01-05
> **jiggles100 said:**
> Hey there neighbour :)
 
Definitely something weird going on there.
 
Can you take one of the repository addresses and paste it into your browser?  It's all http stuff so you should at least see an index page with a list of folders.
 
e.g [http://gb.archive.ubuntu.com/](http://gb.archive.ubuntu.com/)
 
  That should confirm that the issue isn't a connection problem and your ping results aren't an ICMP block by the uni.
 
Are you trying to do the update at the same time of day?  Clutching at straws but it might be a peak time problem.  I'll try to pop past on the way home.


Hey,

Thanks for coming onto the forum :) Yes, I can take one of the repository addresses and paste it into my browser not a problem and I get an index page.

Just tried running sudo apt-get update and again it doesn't seem to connect to the mirror :

Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) intrepid Release.gpg                      
  Could not connect to apsy.gse.uni-magdeburg.de:80 (141.44.96.210), connection timed out
Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) intrepid/main Translation-en_GB           
  Unable to connect to apsy.gse.uni-magdeburg.de http:
Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) intrepid/non-free Translation-en_GB       
  Unable to connect to apsy.gse.uni-magdeburg.de http:
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
  Unable to connect to archive.canonical.com http:
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid Release.gpg                              
  Could not connect to ftp.de.debian.org:80 (141.76.2.4), connection timed out
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid/main Translation-en_GB                   
  Unable to connect to ftp.de.debian.org http:
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid/non-free Translation-en_GB               
  Unable to connect to ftp.de.debian.org http:
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) intrepid/contrib Translation-en_GB                
  Unable to connect to ftp.de.debian.org http:

Frustrating!! Have been trying to update at various times of the day to no avail. Have spoken to the uni IT and they got me to change some proxy settings and to add one which I did via Preferences/network Proxy as well as in the synpatic package manager preferences. Still getting the above...

---

### Post by jiggles100 on 2010-01-05
Hmm, I'm always wary of proxy servers ... you never know what they are blocking.  I wonder if anybody from AberLUG can help with deciphering the network topology.

---

### Post by jiggles100 on 2010-01-05
After a little digging it may be something to do with proxy.

Can you run the following command in a terminal:

```
sudo apt-config dump
```

You might find [this blog link]("http://raetsel.wordpress.com/2006/10/29/laptop-build-apt-get-behind-a-proxy/") of some value to your investigations.

Let me know if you need further assistance ;)

---

### Post by Aberdeen-linux on 2010-01-06
Unfortunately still no joy. I looked at the blog and followed the changes they made and it still doesn't work. ARGGGG...

---

