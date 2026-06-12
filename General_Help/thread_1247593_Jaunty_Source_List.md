---
title: "Jaunty Source List"
date: 2009-08-23
forum: General Help
---

### Post by buzz263 on 2009-08-23
I was trying to add E17 to my setup, and in the process I messed up my source list.  Can anyone up a basic Jaunty 32bit list, as it is right now my system will not update at all.

Thanks for the help!

Brent
'buzz263'

---

### Post by VCoolio on 2009-08-23
Here is the default part of mine; note that it uses a Dutch (nl) repo, you may want to change that to something closer to you. Also universe and multiverse repos are activated.

```
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

---

### Post by buzz263 on 2009-08-23
Many Thanks for the super fast response!

Brent
'buzz263'

---

### Post by jerrrys on 2009-08-23
an easy way

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by buzz263 on 2009-08-24
Another great find, but now i have a new problem.  This is the error I get when trying to update

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Again, thanks for any help in bailing this newbie out!

Brent
'buzz263'

---

### Post by jerrrys on 2009-08-24
just do what it said and run **sudo dpkg --configure -a **in terminal (accessories>terminal)

---

### Post by buzz263 on 2009-08-24
I tried that and had a bad address for e17 causing a failure.  I removed e17 thru synaptic, added my newly updated sources list (nice site!), and everything seems to be back to normal.

I'm still pretty new to linux, can you tell?  But I can say this, we are now a Ubuntu family, all of us prefer this over windows. 

This excellent OS has made a believer out of me, it's just that I'm back in learning mode!

Thank you for all of your help!

Brent
'buzz263'

---

