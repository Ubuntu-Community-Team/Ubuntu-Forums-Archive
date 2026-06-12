---
title: "E:Malformed line 52 in source list /etc/apt/sources.list (URI), E:The list of sources"
date: 2011-10-31
forum: General Help
---

### Post by ZacoOne on 2011-10-31
I am trying to update but when I try to open the Update Manager I get the following error:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 52 in source list /etc/apt/sources.list (URI), E:The list of sources could not be read.'

Please help...

---

### Post by 3rdalbum on 2011-10-31
Looks like you've added something to line 52 of the file '/etc/apt/sources.list' that isn't formed correctly.

Open up that file as root (put this into the terminal):

```
gksudo gedit /etc/apt/sources.list
```

There's a mistake on **or around** line 52. All lines must start with "deb", "deb-src" or "#". If you can't see the problem, then copy and paste the contents of the file into a message here and we'll take a look at it.

If you remove the offending line, you need to save your changes by clicking the Save button at the top of the window and then running this terminal command:

```
sudo apt-get update
```

Then everything will work again properly, assuming the bad line has been removed.

In future, if you want to add repositories to your system, go into Software Center. Go to the Edit menu and then Software Sources. Use this program to add repositories - it doesn't let you add any malformed lines.

---

### Post by ZacoOne on 2011-11-03
It looks like I only have 45 lines. What am I missing? Here's the list...

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe #Added by software-properties
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic
# Fingerprint reader support (fprint)
deb
[http://ppa.launchpad.vet/madman2k/ubuntu](http://ppa.launchpad.vet/madman2k/ubuntu) hardy main restricted universe
multiverse

---

### Post by PaulW2U on 2011-11-03
You have 54 lines if you count the blank ones. :)

The following should all be one one line.

```
deb
http://ppa.launchpad.vet/madman2k/ubuntu hardy main restricted universe
multiverse
```

---

### Post by ZacoOne on 2011-11-03
It's working. Thank you for the help! :D

---

