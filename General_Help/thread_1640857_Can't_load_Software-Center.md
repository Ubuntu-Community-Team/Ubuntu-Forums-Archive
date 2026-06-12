---
title: "Can't load Software-Center"
date: 2010-12-08
forum: General Help
---

### Post by Don DeGregori on 2010-12-08
Just installed 10.10. Notice Software Center is seen at bottom of Applications. It seems to load, but after a bit it quits. I removed it with Synaptic, and reinstalled. Same problem. All normal updates have been installed.
What's going here?
Don

---

### Post by philinux on 2010-12-08
> **Don DeGregori said:**
> Just installed 10.10. Notice Software Center is seen at bottom of Applications. It seems to load, but after a bit it quits. I removed it with Synaptic, and reinstalled. Same problem. All normal updates have been installed.
What's going here?
Don

Open a terminal. Apps>accessories>Terminal and run it from there.

```
software-center
```

Post back any errors.

Also try this and see if any errors.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Don DeGregori on 2010-12-08
Here is what I get.

donde@donde-desktop:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 62, in <module>
    from view.logindialog import LoginDialog
  File "/usr/share/software-center/softwarecenter/view/logindialog.py", line 30, in <module>
    from softwarecenter.backend.launchpad import GLaunchpad
  File "/usr/share/software-center/softwarecenter/backend/launchpad.py", line 32, in <module>
    from launchpadlib.launchpad import Launchpad
  File "/usr/lib/pymodules/python2.6/launchpadlib/launchpad.py", line 28, in <module>
    from lazr.uri import URI
ImportError: No module named uri
donde@donde-desktop:~$ 

And with next command

donde@donde-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for donde: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [65B]
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Fetched 65B in 1s (42B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
donde@donde-desktop:~$

---

### Post by philinux on 2010-12-08
From the terminal.

```
sudo apt-get install --reinstall app-install-data
```

Then try software centre.

---

### Post by Don DeGregori on 2010-12-08
Phil
Did what you last said. Still No Joy. Re-did last command again. No errors.
Don

---

### Post by philinux on 2010-12-08
> **Don DeGregori said:**
> Phil
Did what you last said. Still No Joy. Re-did last command again. No errors.
Don

Try deleting this folder.

/home/**yourusername**/.cache/software-center

It will get recreated when you start up SC.

---

### Post by Don DeGregori on 2010-12-08
Phil,
Did what last said. Went to:
cd /home/donde/.cache
Then:
sudo rm -r software-center
This worked. Restarted 10.10
Tried software center.
Got whirling little circle for awhile and then it quit to mouse pointer.
Don

---

### Post by Don DeGregori on 2010-12-08
Got to go now, but please help me with some more ideas. Be back in an hour or so.

Don

---

### Post by philinux on 2010-12-08
From the terminal try running it like this.

```
gksudo software-center
```

I'm running out of ideas on this.

Also post back what this says.

```
cat /etc/lsb-release
```
And

```
cat /etc/apt/sources.list
```

---

### Post by Don DeGregori on 2010-12-08
OK, I'm back

Here's what I get

donde@donde-desktop:~$ gksudo software-center
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 62, in <module>
    from view.logindialog import LoginDialog
  File "/usr/share/software-center/softwarecenter/view/logindialog.py", line 30, in <module>
    from softwarecenter.backend.launchpad import GLaunchpad
  File "/usr/share/software-center/softwarecenter/backend/launchpad.py", line 32, in <module>
    from launchpadlib.launchpad import Launchpad
  File "/usr/lib/pymodules/python2.6/launchpadlib/launchpad.py", line 28, in <module>
    from lazr.uri import URI
ImportError: No module named uri
donde@donde-desktop:~$ 

And,

donde@donde-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
donde@donde-desktop:~$ 

And,

donde@donde-desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
donde@donde-desktop:~$ 

Sure appreciate your patience :p
Don

---

### Post by philinux on 2010-12-08
Try this.

```
sudo apt-get install python-launchpadlib
```
Then try SC.

From here. [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/634324](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/634324)

---

### Post by Don DeGregori on 2010-12-08
Phil,

donde@donde-desktop:~$ sudo apt-get install python-launchpadlib
[sudo] password for donde: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-launchpadlib is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
donde@donde-desktop:~$ 

Tried SC. Still trys to load, but doesn't. No errors seen.
Darn! 

Don

---

### Post by IronHide NSDQ on 2010-12-09
I am having the exact same problem!! 

Hope we can get this sorted!

---

### Post by Don DeGregori on 2010-12-09
Well, I finally got it fixed. Always noticed the burn to CD was very slow. Even the procedure of having to close CD Creator, and then clicking on Write to Disk is confusing. Then I noticed strange error message of can't unmount disk, or the burn program wanted to start over again doing a checksum. This problem was leading me in circles. Thought the CD burner was bad or MB  hardware. So, tried external CD. It seemed different tests yielded different questions of what was bad, nothing clearcut.

Well, enough is enough! Decided to return to normal. Downloaded 10.10 all over again. It went into Download folder. Put in fresh CD-R. Right clicked on iso, selected Write to Disk. Cancel "Disk Creator", clicked on Burn. From then on everything went smoother and faster. Put in LiveCD. Saw Software Center. Then, did Install, no problem. Software Center still there. (New install is kind of weird)

This the 1st time I've had any kind of install problem with Ubuntu, after probably 20 different Ubuntu installs over the years. The apparently "bad" download was from the UK. I wish we could choose the least distant  repository, like we used to.  

And I think the process of burning a CD is still very confusing. Never do I see Write speed, or a way to change it. No time indication of progress. No indication of what's going on at all, except that stupid orange bar moving back and forth. And what does it mean "Write to Disk? Does that mean Hard Drive at the same time as Burning to Disk? Canonical has really dumbed down this application. Every statement should be explicit, and if an error happens, it should tell you in plain terms, what it is. I know MS has given us cryptic error messages for 30 years. Ubuntu should get better at it!

So, maybe what came out of the UK server that fateful day was a bit corrupted! Keep on 'trucking everyone (downloading).  :)

Don

---

### Post by andrikos on 2011-01-10
I had a similar problem which was fixed by doing:

sudo apt-get --reinstall install python-lazr.uri python-lazr.restfulclient

---

