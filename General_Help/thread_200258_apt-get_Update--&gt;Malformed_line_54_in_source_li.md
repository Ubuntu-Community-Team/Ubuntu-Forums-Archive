---
title: "apt-get Update--&gt;Malformed line 54 in source list"
date: 2006-06-20
forum: General Help
---

### Post by nealklomp on 2006-06-20
two thread started for help in one day! First time for anything I suppose.
Anyway, I tried to use add/remove app and got: 
```
**Failed to check for installed and available applications**
This is a magor failure of your software management system.
Check permissions and correctness of the file '/etc/apt/sources.list'
 and reload the software information: 'sudo apt-get update'. 
```

Took a look at '/etc/apt/sources.list' for an obvious issue saw nothing wrong:
```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu/ dapper-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse

deb http://wine.lowvoice.nl/apt dapper main
deb-src http://wine.lowvoice.nl/apt dapper main

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 dapper main

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ dapper/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ dapper/

deb http://theli.free.fr/packages/dapper/ ./
## created by arniewinechanged
# Repository for wine
deb http://wine.sourceforge.net/apt binary/
deb-src http://wine.sourceforge.net/apt source/


_***deb http://archive.ubuntu.com/ubuntu_***
deb-src http://archive.ubuntu.com/ubuntu
deb http://packages.freecontrib.org/ubuntu/plf
deb-src http://packages.freecontrib.org/ubuntu/plf

```
(line 54 underlined, bold and italics)
so ran 
```
sudo apt-get update
```
which returned
```
E: Malformed line 54 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.

```

I had recently done some expanding of sources and isntalled that planetarium thing.

anyway anyone want to take a look at their /etc/apt/sources.list and tell me where mine differs?
otherwise I might try lopping off at line 54.

---

### Post by aysiu on 2006-06-20
This is what mine looks like. Notice how there are random words after every web address? The web address alone is not enough: ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free 
```

---

### Post by nealklomp on 2006-06-20
yeah I think I'll just take off everything after 53. What's the worst that can happen now?

by the bye, Aysiu, I like two things very much that you have done, well now three, the sticker about unanswered threads, and the Gnome KDE comparison.
I've played with both and will be considering if I have anything to offer, as I read it.

Edit, yeah that did the trick. Could've not posted, must be becoming a habit.

Desire to contribute, but lacking the expertise to help others, but have the ability to help myself.

---

