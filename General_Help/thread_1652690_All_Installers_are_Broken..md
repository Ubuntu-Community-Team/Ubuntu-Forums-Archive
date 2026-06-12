---
title: "All Installers are Broken."
date: 2010-12-25
forum: General Help
---

### Post by Orlsend on 2010-12-25
So when I try to install something either by aptitude,apt-get,Synaptic or individual .debs the task will stop and give out an error out-put

```
E: Read error - read (5: Input/output error) E: The package lists or status file could not be parsed or opened. E: _cache->open() failed, please report.
```

I decided reinstall the Ubuntu 10.10, yet after installing a few apps the installers get corrupted.

I tried all the able commands to normal fix like these.
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove
```

No prevail, so I decided to check my HD just in case but its all fine!

Here are my Software sources just in case.

```
paez@paez-900HA:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://tn.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://tn.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://tn.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://tn.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://tn.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://tn.archive.ubuntu.com/ubuntu/ maverick universe
deb http://tn.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://tn.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://tn.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://tn.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://tn.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://tn.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://tn.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://tn.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

```

I ran out of Ideas, anyone got any?

---

### Post by wojox on 2010-12-25
> No prevail, so I decided to check my HD just in case but its all fine!

You ran 

```
sudo touch /forcefsck
```

And rebooted?

---

### Post by Orlsend on 2010-12-25
Yeah that what I meant :).

yeah I tried that.

---

### Post by PJ M on 2010-12-25
Have similar problem after downloading keep getting error message like the one below when I was trying to install software from a disk facilitating transfer from video tape to dvd -


Archive:  /media/IDVDR/InstantDVDRecorder/Setup.exe
[/media/IDVDR/InstantDVDRecorder/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/IDVDR/InstantDVDRecorder/Setup.exe or
          /media/IDVDR/InstantDVDRecorder/Setup.exe.zip, and cannot find /media/IDVDR/InstantDVDRecorder/Setup.exe.ZIP, period.

No problem installing ubuntu software.

_Not prompted to authenticate either l_ike when installing ubuntu software.

This seems to apply to all software after downloading

---

### Post by TeoBigusGeekus on 2010-12-25
What about [this]("http://forums.linuxmint.com/viewtopic.php?f=47&t=34568&p=199618")?

---

### Post by Rubi1200 on 2010-12-25
> **Orlsend said:**
> Yeah that what I meant :).

yeah I tried that.
Did you try updating again after rebooting?

---

### Post by karthick87 on 2010-12-25
Try this,
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
```
sudo apt-get update && sudo apt-get upgrade
```

Post the complete output,if you get any error.

---

### Post by PJ M on 2010-12-25
Thanks for reply

exuse my ignorance but how do I do this?
PJ M

---

### Post by Orlsend on 2010-12-25
> paez@paez-900HA:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
paez@paez-900HA:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                        
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                    
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick Release.gpg
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages      
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://tn.archive.ubuntu.com/ubuntu/](http://tn.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick Release
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick/main Sources
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick/restricted Sources
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick/universe Sources
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://tn.archive.ubuntu.com](http://tn.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

Thats what happend

---

### Post by karthick87 on 2010-12-25
Did you run my first command??

---

### Post by matt_symes on 2010-12-25
Hi

Have a look at this

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/66668](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/66668)

Kind regards

---

### Post by wojox on 2010-12-25
A little more dated [read error-read(5:input/output error)]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/115082")

---

### Post by killertm on 2012-06-24
this is about the same thing thats happening to me and none of those codes really did anything other than come up with "could not be parsed or opened"

---

