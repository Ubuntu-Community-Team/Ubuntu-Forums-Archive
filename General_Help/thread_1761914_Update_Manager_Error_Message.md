---
title: "Update Manager Error Message"
date: 2011-05-18
forum: General Help
---

### Post by AnneElizabeth on 2011-05-18
I am relatively new to Ubuntu, so this might be an easy fix...
When I try to install my updates with Update Manager I get this error message:

  	 	 	 	p { margin-bottom: 0.08in; }  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-pulse_1.0.6-1ubuntu1.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-pulse_1.0.6-1ubuntu1.3_i386.deb) 
   Could not connect to 172.16.30.51:3128 (172.16.30.51). - connect (110: Connection timed out)  
 

 

 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.6-1ubuntu1.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.6-1ubuntu1.3_i386.deb) 
   Unable to connect to 172.16.30.51:3128: 



(and it goes on like this for a while)




Also, when I go to install software, I get this message:


Requires installation of untrusted packages.


...and if I click OK, nothing happens.  The software won't install.  I have a feeling this is because I can't update my system.  Yes?


Please help.

---

### Post by dabl on 2011-05-18
Follow this:  [http://ubuntuforums.org/showthread.php?p=10833160#post10833160](http://ubuntuforums.org/showthread.php?p=10833160#post10833160)

---

### Post by AnneElizabeth on 2011-05-18
I did this (above link), and got the same error messages in the terminal...

Unable to connect to 172.16.30.51:3128:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plug](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plug)

and lots more like that.

I still have Ubuntu 10.04, so I don't think this has to do with the upgrade issue other people seem to be having with update manager.

What else ya got?
(thank you, by the way)

---

### Post by dabl on 2011-05-18
> **AnneElizabeth said:**
> 

What else ya got?
(thank you, by the way)


I got "your source list ain't right".  :D

It would appear a non-official source, the name of which ends in "vlc-plug", has been inserted into your source list.  To get a working, stable system, I suggest you go back to the default natty (I assume you are using ver. 11.04) source list, i.e. the file /etc/apt/sources.list, which looks like this (including the "partner" and "extras" repos):

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main
```

Also, if there are any active source repos in the /etc/apt/sources.list.d/ directory, I recommend you disable them for the time being. Once your system is upgrading correctly, you can carefully add back additional sources, one at a time, watching for errors.

---

### Post by wildmanne39 on 2011-05-18
> **AnneElizabeth said:**
> I am relatively new to Ubuntu, so this might be an easy fix...
When I try to install my updates with Update Manager I get this error message:

  	 	 	 	p { margin-bottom: 0.08in; }  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-pulse_1.0.6-1ubuntu1.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-pulse_1.0.6-1ubuntu1.3_i386.deb) 
   Could not connect to 172.16.30.51:3128 (172.16.30.51). - connect (110: Connection timed out)  
 

 

 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.6-1ubuntu1.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_1.0.6-1ubuntu1.3_i386.deb) 
   Unable to connect to 172.16.30.51:3128: 



(and it goes on like this for a while)




Also, when I go to install software, I get this message:


Requires installation of untrusted packages.


...and if I click OK, nothing happens.  The software won't install.  I have a feeling this is because I can't update my system.  Yes?


Please help.
Hi, what version of ubuntu is that if it is an old one those repositories are not still available, you can also change the server you are trying to download from. The vlc link is not good, do what the post says above mine and it should fix the problem.

---

### Post by Larkspur on 2011-05-18
vlc-plugins-pulse is in the Universe repo.  My guess is that you just need to reload your sources: go to Software Sources, make sure the normal repositories are checked, and click close.  It will tell you it needs to update, click to allow it to.  Alternatively, open Synaptic and click "reload".

---

