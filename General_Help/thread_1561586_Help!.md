---
title: "Help!"
date: 2010-08-26
forum: General Help
---

### Post by LegendaryCurse on 2010-08-26
I dont even know if this is the right area, I was trying to install skype and it said I had to make sure everything was setup in the packet manager, and then when I went to close out and install skype I got this.

E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Along side of that I get this in the update manager.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 5 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read.'


HELP ITS MY FIRST TIME TODAY USING UBUNTU !!!

---

### Post by howefield on 2010-08-26
Skype is in the partner repository, so should just be a case of enabling it and installing.

But to sort your sources.list first, can you open a terminal, (Applications > Accessories > Terminal) and type

```
gksudo gedit /etc/apt/sources.list
```

Enter your password if prompted, you won't see it being typed but it is, and post the contents of sources.list back here ?

---

### Post by LegendaryCurse on 2010-08-26
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb Canada lucid main restricted
deb-src Canada lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb Canada lucid-updates main restricted
deb-src Canada lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb Canada lucid universe
deb-src Canada lucid universe
deb Canada lucid-updates universe
deb-src Canada lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb Canada lucid multiverse
deb-src Canada lucid multiverse
deb Canada lucid-updates multiverse
deb-src Canada lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb Canada lucid-security main restricted
deb-src Canada lucid-security main restricted
deb Canada lucid-security universe
deb-src Canada lucid-security universe
deb Canada lucid-security multiverse
deb [http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/) lucid main universe restricted multiverse
deb-src Canada lucid-security multiverse

---

### Post by howefield on 2010-08-26
In terminal type

```
gksudo gedit /etc/apt/sources.list
```

Place a hash sign # in front of line 5. The one that goes... deb Canada lucid main restricted.

Save the file,  close and try again, I suspect you have many malformed lines in there, so you may have to repeat the process a few times. I don't recognise much of what you have in there.

---

### Post by LegendaryCurse on 2010-08-26
Just in that one line ?
Or do I put a # in front of all the lines that say "deb Canada lucid main restricted" ?

---

### Post by howefield on 2010-08-26
> **LegendaryCurse said:**
> Just in that one line ?
Or do I put a # in front of all the lines that say "deb Canada lucid main restricted" ?

Your choice, the error relates to line 5, but I think you will have a list of errors taking you down the page. You'll fix line 5, then line 6 will error, and so on. If it were mine, I'd put a # in front of all lines that didn't have http in them.

---

### Post by LegendaryCurse on 2010-08-26
[SOLVED]

I just took your advice what you said and applied a # infron of everything and sure enough all there errors went away skype installed and it updated.
Thanks dude much appreciated +

---

