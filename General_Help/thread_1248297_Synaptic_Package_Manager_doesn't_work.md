---
title: "Synaptic Package Manager doesn't work"
date: 2009-08-24
forum: General Help
---

### Post by maTvey on 2009-08-24
E: Type 'echo' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report


PLEASE HELP

---

### Post by oboedad55 on 2009-08-24
> **maTvey said:**
> E: Type 'echo' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

You need to edit your sources.list and remove the offending line.

---

### Post by j7%&lt;RmUg on 2009-08-24
Post your sources.list file here, then i can help you.

Lol posted at the same time, the above poster is correct.

---

### Post by sahabcse on 2009-08-24
Hi

Add the repositories in synaptic setting menu, then click reload for resolving this issue. Using synaptic manager pls follow below url

[http://ubuntulinux.co.in/package-instalation-synaptic.php](http://ubuntulinux.co.in/package-instalation-synaptic.php)

---

### Post by maTvey on 2009-08-24
[quote=oboedad55;7836865]You need to edit your sources.list and remove the offending line.[/quot 

how to do it? i'm new in linux

---

### Post by maTvey on 2009-08-24
> **sahabcse said:**
> Hi

Add the repositories in synaptic setting menu, then click reload for resolving this issue. Using synaptic manager pls follow below url

[http://ubuntulinux.co.in/package-instalation-synaptic.php](http://ubuntulinux.co.in/package-instalation-synaptic.php)
   
i can't do nothin, it gives me the error when i open it - E: Type 'echo' is not known on line 50 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by j7%&lt;RmUg on 2009-08-24
Ok ill explain some more.

open a terminal and type:
```

sudo gedit /etc/apt/sources.list

```

Then find line 50 and remove the "echo" that synaptic cant recognize, save it and exit.

Then type:
```

sudo apt-get update

```

Let us know what happens.

---

### Post by maTvey on 2009-08-24
i remove line 50, and when i type sudo apt-get update  this comes out - sudo' is not known on line 47 in source list /etc/apt/sources.list

---

### Post by sahabcse on 2009-08-24
Hi

Try the following

#sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
#sudo gedit /etc/apt/sources.list


then paste the following and save it

------------------------------------------
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
---------------------------------------------------------------

Then run

#sudo apt-get update

---

### Post by j7%&lt;RmUg on 2009-08-24
Like the above post says, please backup and post your sources.list then we can help you edit out the non-recognized parts.

---

### Post by maTvey on 2009-08-24
> **sahabcse said:**
> hi

try the following

#sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
#sudo gedit /etc/apt/sources.list


then paste the following and save it

------------------------------------------
# deb cdrom:[ubuntu 9.04 _jaunty jackalope_ - release i386 (20090420.1)]/ jaunty main restricted
# see [http://help.ubuntu.com/community/upgradenotes](http://help.ubuntu.com/community/upgradenotes) for how to upgrade to
# newer versions of the distribution.

Deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty main restricted

## major bug fix updates produced after the final release of the
## distribution.
Deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## n.b. Software from this repository is entirely unsupported by the ubuntu
## team. Also, please note that software in universe will not receive any
## review or updates from the ubuntu security team.
Deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## n.b. Software from this repository is entirely unsupported by the ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse will not receive any review or updates from the ubuntu
## security team.
Deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## uncomment the following two lines to add software from the 'backports'
## repository.
## n.b. Software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## also, please note that software in backports will not receive any review
## or updates from the ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## uncomment the following two lines to add software from canonical's
## 'partner' repository.
## this software is not part of ubuntu, but is offered by canonical and the
## respective vendors as a service to ubuntu users.
Deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
---------------------------------------------------------------

then run

#sudo apt-get update

thanks a lot!  Now it works.

---

