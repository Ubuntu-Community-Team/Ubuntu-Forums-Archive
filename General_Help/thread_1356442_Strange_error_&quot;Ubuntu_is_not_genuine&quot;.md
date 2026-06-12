---
title: "Strange error &quot;Ubuntu is not genuine&quot;"
date: 2009-12-16
forum: General Help
---

### Post by pluto4ps on 2009-12-16
Hi,
I installed Ubuntu on one of my Desktop.
Installation went fine.
Restarted the desktop.
After booting to desktop, Crash Report generated and when I clicked to submit I got pop up message that "THIS UBUNTU IS NOT GENUINE" message cannot be submitted....

I did not understand what happened?

---

### Post by Physical Hook on 2009-12-16
I guess it's [COLOR=Green]This not a genuine Ubuntu package[/COLOR], not [COLOR=Green]Ubuntu is not genuine[/COLOR] ? Check this [bug report]("https://bugs.launchpad.net/ubuntu/+bug/157720").

---

### Post by pluto4ps on 2009-12-16
does it mean I need to re-install the OS???

---

### Post by philinux on 2009-12-16
> **pluto4ps said:**
> does it mean I need to re-install the OS???

No but next time you need to accurately record the error message.

It was likely a piece of software was not authenticated as from ubuntu repo.

Open a terminal and post the output of this.

```
cat /etc/apt/sources.list
```

---

### Post by pluto4ps on 2009-12-16
Output of the code: 
cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by philinux on 2009-12-16
That looks fine. Have any files inside this folder.

```
ls /etc/apt/sources.list.d

```

---

### Post by pluto4ps on 2009-12-16
opera.list

This is what I got in terminal...

---

### Post by pluto4ps on 2009-12-16
After installing Ubuntu, the first time logged in desktop, I got this error message and after that as normal it got updated with all the updates, but I was worried about that error message. 

I don't know why on the first login it created crash report and this message?

---

### Post by philinux on 2009-12-16
> **pluto4ps said:**
> opera.list

This is what I got in terminal...

Ok so.

```
cat /etc/apt/sources.list.d/opera.list
```

Also post back any errors from this.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by pluto4ps on 2009-12-16
cat /etc/apt/sources.list.d/opera.list



# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free

---

### Post by pluto4ps on 2009-12-16
sudo apt-get update && sudo apt-get upgrade

Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_IN          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release                     
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by philinux on 2009-12-16
All fine and dandy then. No worries.

If it happens again screen print the error.

You probably got it as opera is not part of the ubuntu repo system.

---

### Post by pluto4ps on 2009-12-16
Thanks for your help...I appreciate it....

---

