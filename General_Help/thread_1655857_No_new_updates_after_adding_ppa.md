---
title: "No new updates after adding ppa"
date: 2010-12-30
forum: General Help
---

### Post by McBraid on 2010-12-30
While trying to get my wwan to work i somehow messed up. I got a some errors when running apt-get update. I disabled the source causing the errors and I can now update normally. However, it's been over a week and no available updates has been presented by the update manager. This makes me think that something is wrong.

The now disabled source, causing the most recent error was;
```
W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

```

No other software sources has been disabled. So regular updates should be working.

Here is some command line outputs that might be relevant:

ls /etc/apt/sources.list.d
```
dropbox.list
dropbox.list.save
gwibber-daily-ppa-maverick.list
gwibber-daily-ppa-maverick.list.save
linrunner-thinkpad-extras-maverick.list
linrunner-thinkpad-extras-maverick.list.save
user-ppa-name-maverick.list
user-ppa-name-maverick.list.save

```

cat /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://se.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://se.archive.ubuntu.com/ubuntu/ maverick universe
deb http://se.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://se.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://se.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://se.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

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

```

apt-get update after disabling the source causing the error: 
```

Hit http://se.archive.ubuntu.com maverick Release.gpg
Ign http://se.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://se.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://se.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://se.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://se.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu/ maverick/main Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://se.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://se.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://se.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://se.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://archive.canonical.com maverick Release                              
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://se.archive.ubuntu.com maverick-backports Release.gpg                
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Hit http://extras.ubuntu.com maverick/main Sources                             
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://se.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://se.archive.ubuntu.com maverick Release                              
Hit http://se.archive.ubuntu.com maverick-updates Release                      
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://se.archive.ubuntu.com maverick-backports Release                    
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://se.archive.ubuntu.com maverick/main Sources                         
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://se.archive.ubuntu.com maverick/restricted Sources
Hit http://se.archive.ubuntu.com maverick/universe Sources
Hit http://se.archive.ubuntu.com maverick/multiverse Sources
Hit http://se.archive.ubuntu.com maverick/main i386 Packages
Hit http://se.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://se.archive.ubuntu.com maverick/universe i386 Packages
Hit http://se.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://se.archive.ubuntu.com maverick-updates/main Sources
Hit http://se.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://se.archive.ubuntu.com maverick-updates/universe Sources
Hit http://se.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://se.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://se.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://se.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://se.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://se.archive.ubuntu.com maverick-backports/main i386 Packages
Hit http://se.archive.ubuntu.com maverick-backports/restricted i386 Packages
Hit http://se.archive.ubuntu.com maverick-backports/universe i386 Packages
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US
Hit http://se.archive.ubuntu.com maverick-backports/multiverse i386 Packages
Hit http://linux.dropbox.com maverick Release
Hit http://linux.dropbox.com maverick/main i386 Packages
Reading package lists... Done

```

Any suggestions on how to attack this issue?

---

### Post by plucky on 2010-12-30
> Any suggestions on how to attack this issue? 

What Issue?

You had a problem with the PPA which you corrected.That would have stopped update manager working correctly.

"sudo apt-get update" showed no errors.

What does ```
sudo apt-get upgrade
``` show you?

I have not had any updates on Maverick since 22nd December until today,when there was a kernel upgrade.The update manager will only show updates every day only if there are "security updates",for normal distribution updates,it will only show you once a week.

Good Luck

---

### Post by mcduck on 2010-12-30
I don't think there is a PPA repository called "ppa-name"... ;)

You should probably replace that with the actual name of the repository you wish to add...

---

### Post by McBraid on 2010-12-30
The issue i was referring to was this thread in general.

sudo apt-get upgrade results in:
```
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

> The update manager will only show updates every day only if there are "security updates",for normal distribution updates,it will only show you once a week.

I've been manually checking for updates on a daily basis.

---

### Post by McBraid on 2010-12-30
> **mcduck said:**
> I don't think there is a PPA repository called "ppa-name"... ;)

You should probably replace that with the actual name of the repository you wish to add...

Yep, seems reasonable. Probably made that mistake by copy-pasting without properly reading first. Oh well, a lesson learned :P

---

### Post by mcduck on 2010-12-30
> **McBraid said:**
> The issue i was referring to was this thread in general.

sudo apt-get upgrade results in:
```
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```



I've been manually checking for updates on a daily basis.

If there are no updates at the moment, you of course won't get any. :)

(s far as I know there hasn't been any security fixes recently. Things are fine at the moment, nothing to repair. :D)

---

### Post by QLee on 2010-12-30
> **mcduck said:**
> I don't think there is a PPA repository called "ppa-name"... ;)

You should probably replace that with the actual name of the repository you wish to add...

Yes, and in addition to that, there is no directory named /user/, so you would have to amend your URL to the name of the user that has posted the ppa you desire.

---

### Post by McBraid on 2010-12-30
Yes, but I have often gotten minor package updates on a regular basis when checking manually. Seems unreasonable that no packages, related to any software component, have been updated for quite some time.

---

### Post by mcduck on 2010-12-30
> **McBraid said:**
> Yes, but I have often gotten minor package updates on a regular basis when checking manually. Seems unreasonable that no packages, related to any software component, have been updated for quite some time.

You mean it's unreasonable that no new security problems have been found recently? :D

The basic rule is that after release Ubuntu versions only get updates to provide security fixes and to fix serious bugs. Never just to give you the latest program version or new features.

---

### Post by McBraid on 2010-12-30
But I've done many package updates (such as a upgrading to a newer version of chromium) through the update manager. These updates has nothing to do with the security of the Ubuntu OS but has still been available for download in the update manager.

---

### Post by mcduck on 2010-12-30
> **McBraid said:**
> But I've done many package updates (such as a upgrading to a newer version of chromium) through the update manager. These updates has nothing to do with the security of the Ubuntu OS but has still been available for download in the update manager.

The you either have a 3rd-party repository for Chromium, or the update actually has been a security update.

---

### Post by McBraid on 2010-12-30
Yes the chromium update is from a third party repo. I have many 3rd party repos. Many of the packages installed from them has been updated through the UM. But not anymore.

---

### Post by mcduck on 2010-12-30
> **McBraid said:**
> Yes the chromium update is from a third party repo. I have many 3rd party repos. Many of the packages installed from them has been updated through the UM. But not anymore.

The 3rd party repositories are maintained by individual people, so they update when the maintainer chooses so. I'd think that many people have other things to think about at this time of the year...

The apt-get update output from your first post shows that all repositories are working just fine. So you really can just relax, the updates will come when there is something to update. :)

---

