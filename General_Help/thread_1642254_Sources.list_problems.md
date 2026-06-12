---
title: "Sources.list problems"
date: 2010-12-10
forum: General Help
---

### Post by patman0623 on 2010-12-10
Hey guys, I've been having trouble with my apt sources for a while now. There are a bunch of vital packages I don't have access to (e.g. ubuntu desktop, folder sharing), and I'm afraid I don't know why. I'll give you a screen dump of my *apt-get update*; perhaps you all could be so kind as to help find the issue? Thanks.

```
$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [197B]
Get:2 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Get:3 http://extras.ubuntu.com maverick Release.gpg [65B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en_US
Get:5 http://us.archive.ubuntu.com maverick-updates Release.gpg [198B]         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:6 http://security.ubuntu.com maverick-security Release [27.2kB]            
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com maverick Release                              
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://extras.ubuntu.com maverick Release                                  
Get:7 http://dl.google.com stable Release.gpg [198B]                           
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/maverick Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/maverick Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Hit http://packages.medibuntu.org maverick Release.gpg                         
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Get:8 http://ppa.launchpad.net maverick Release [9,770B]                       
Get:9 http://dl.google.com stable Release [1,347B]                             
Get:10 http://dl.google.com stable Release [1,347B]                            
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Get:11 http://dl.google.com stable/main i386 Packages [1,066B]                 
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Get:12 http://us.archive.ubuntu.com maverick-updates Release [31.4kB]          
Get:13 http://ppa.launchpad.net maverick/main i386 Packages [3,743B]           
Get:14 http://dl.google.com stable/main i386 Packages [733B]                   
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://us.archive.ubuntu.com maverick Release                              
Get:15 http://security.ubuntu.com maverick-security/main Sources [16.6kB]      
Hit http://us.archive.ubuntu.com maverick/multiverse Sources                   
Get:16 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:17 http://security.ubuntu.com maverick-security/universe Sources [4,985B]
Get:18 http://security.ubuntu.com maverick-security/multiverse Sources [649B]  
Get:19 http://security.ubuntu.com maverick-security/main i386 Packages [52.7kB]
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US             
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages             
Get:20 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:21 http://security.ubuntu.com maverick-security/universe i386 Packages [20.1kB]
Get:22 http://security.ubuntu.com maverick-security/multiverse i386 Packages [1,655B]
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US
Hit http://packages.medibuntu.org maverick Release
Hit http://packages.medibuntu.org maverick/free i386 Packages
Hit http://packages.medibuntu.org maverick/non-free i386 Packages
Fetched 175kB in 2s (68.6kB/s)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release  Unable to find expected entry  maverick/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by sikander3786 on 2010-12-10
Please post the output of,

```
cat /etc/apt/sources.list
```

---

### Post by patman0623 on 2010-12-10
> **sikander3786 said:**
> Please post the output of,

```
cat /etc/apt/sources.list
```

You'll notice there are some commented out lines. I installed Ubuntu from the CDROM, and I've removed that as one of the items. I've also played around just a little to try to fix it, which may explain some of the other lines.
```
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates maverick main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates maverick main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
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
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
# deb http://download.virtualbox.org/virtualbox/debian lucid non-free # disabled on upgrade to lucid
# deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu maverick main # disabled on upgrade to maverick
# deb-src http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main # disabled on upgrade to lucid


## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
# deb http://archive.canonical.com/ubuntu karmic commercial main

deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu maverick main # disabled on upgrade to maverick
#deb http://archive.getdeb.net/ubuntu lucid-getdeb games # disabled on upgrade to maverick

deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
```

---

### Post by sikander3786 on 2010-12-10
Instead of correcting errors in your existing sources.list, I would recommend to create a new one.

Backup your existing sources.list by,

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bad
```

Create a new one.

```
gksudo gedit /etc/apt/sources.list
```

And paste this,

```

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu maverick main # disabled on upgrade to maverick
```

Save and close. And try apt-get update again.

---

### Post by patman0623 on 2010-12-10
> **sikander3786 said:**
> Save and close. And try apt-get update again.Alright, that seems to have fixed something, seeing as I have 38 updates. However, I still have a duplicate sources issue: ```
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by sikander3786 on 2010-12-10
Post the output once more.

```
cat /etc/apt/sources.list
```

---

### Post by snowpine on 2010-12-10
Also check /etc/apt and /etc/apt/sources.list.d/ folders for additional source files and post the contents here, if applicable.

---

### Post by patman0623 on 2010-12-10
> **snowpine said:**
> Also check /etc/apt and /etc/apt/sources.list.d/ folders for additional source files and post the contents here, if applicable.I honestly didn't even know you could sources outside the sources.list file... can you explain how it works? Here's a screendump of my directories:

```
/etc/apt$ ls
apt.conf.d     sources.list~        sources.list.distUpgrade  trusted.gpg~
preferences.d  sources.list_backup  sources.list.save         trusted.gpg.d
secring.gpg    sources.list.bad     trustdb.gpg
sources.list   sources.list.d       trusted.gpg

/etc/apt$ ls sources.list.d
google-chrome.list                  medibuntu.list
google-chrome.list.distUpgrade      medibuntu.list.distUpgrade
google-chrome.list.save             medibuntu.list.save
google-talkplugin.list              pidgin-ppa.list
google-talkplugin.list.distUpgrade  pidgin-ppa.list.distUpgrade
google-talkplugin.list.save         pidgin-ppa.list.save
lucid-partner.list                  ubuntu-wine-ppa-lucid.list
lucid-partner.list.distUpgrade      ubuntu-wine-ppa-lucid.list.distUpgrade
lucid-partner.list.save             ubuntu-wine-ppa-lucid.list.save

```

---

### Post by plucky on 2010-12-10
> lucid-partner.list
lucid-partner.list.distUpgrade 
lucid-partner.list.save 

Remove the lucid-partner.list from the /etc/apt/sources.list.d directory,then run ```
sudo apt-get update
``` and see if the warning still occurs.


Good Luck

---

### Post by patman0623 on 2010-12-10
Ah, that's done it! Thanks so much.

---

### Post by angus_young on 2010-12-10
I'm having a similar problem to the OP

Can anyone help!!, here are my outputs

ls sources.list.d
dropbox.list       google-chrome.list       voria-ppa-maverick.list
dropbox.list.save  google-chrome.list.save  voria-ppa-maverick.list.save


cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates main restricted multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-security main restricted multiverse universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates main restricted multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-security main restricted multiverse universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe


Thanks for any help

---

### Post by plucky on 2010-12-10
@angus_young


What is the error as those lists look ok?

Post output from a terminal for ```
sudo apt-get update
```

p.s. As this thread is marked as [Solved] you might get a better response if you start your own thread.

---

### Post by sikander3786 on 2010-12-11
> **plucky said:**
> Remove the lucid-partner.list from the /etc/apt/sources.list.d directory,then run ```
sudo apt-get update
``` and see if the warning still occurs.


Good Luck
Nice one **plucky**. I couldn't think that lucid-partner could've been causing problems here.

Thanks :-)

---

### Post by oldos2er on 2011-11-19
Closed, necro.

---

