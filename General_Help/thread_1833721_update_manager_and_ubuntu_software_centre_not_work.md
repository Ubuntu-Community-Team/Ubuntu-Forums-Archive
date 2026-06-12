---
title: "update manager and ubuntu software centre not working"
date: 2011-08-26
forum: General Help
---

### Post by jaj540 on 2011-08-26
I cannot download install or remove any softwares using ubuntu software centre.. whenever I try it comes an error like " Items cannot be installed or removed until the package catalog is repaired.do u want to repair it now?" but when i click yes, it comes an error check your internet connection..but actually my internet connection works fine...
And whenever i TRIED TO UPDATE , an error comes like "not all updates can be installed.run a partial update ,to update as many updates as possible... "
but this also fails... even installation using terminal also fails ..."
pls help me..
i am using ubuntu 11.4 and recently installed a package of splashy which didnt worked.... also added some new third party repositories using ubuntu tweak such as backtrack4,remastersys".
can i roll up back to the old normal condition...?

pls help  me... :(

---

### Post by drpjkurian on 2011-08-26
Hi 
I suggest you to try repair broken packages. See whether it solves the problem

---

### Post by Enigmapond on 2011-08-26
You probably updated invalid repos. Try to disable all third party repos and then update. Or Run:

```
cat /etc/apt/sources.list
```

and list the results here.

---

### Post by jaj540 on 2011-08-26
> **Enigmapond said:**
> You probably updated invalid repos. Try to disable all third party repos and then update. Or Run:

```
cat /etc/apt/sources.list
```

and list the results here.
this is the results for the cat /etc/apt/sources.list.How to know unwanted repositories???


abel@PandorasBox:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty main restricted
deb-src [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-updates main restricted
deb-src [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty universe
deb-src [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty universe
deb [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-updates universe
deb-src [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty multiverse
deb-src [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty multiverse
deb [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-updates multiverse
deb-src [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-security main restricted
deb-src [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-security main restricted
deb [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-security universe
deb-src [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-security universe
deb [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-security multiverse
deb-src [http://www.mirror.upm.edu.my/ubuntu/](http://www.mirror.upm.edu.my/ubuntu/) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) maverick main deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) natty main
# deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) maverick main deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) natty main
deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/
deb-src [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) unstable main
deb-src [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) unstable main
abel@PandorasBox:~$

---

### Post by jerrrys on 2011-08-26
step #1

comment out (#) the following lines

deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/
deb-src [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) unstable main
deb-src [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) unstable main

i say step one because you did a partial update and this has left other things broke.

step #2

open a terminal and enter:

sudo apt-get update

and post any errors

---

### Post by raja.genupula on 2011-08-26
> **jerrrys said:**
> step #1

comment out (#) the following lines

deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/
deb-src [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb-src [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) unstable main
deb-src [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) unstable main

i say step one because you did a partial update and this has left other things broke.

step #2

open a terminal and enter:

sudo apt-get update

and post any errors

i am very curious to know that how you have found that they are broken .i mean i dont know & i wanna know about this .

---

### Post by jerrrys on 2011-08-26
i do not know that they are broken, but the OP (are you one of the same?) said that default settings would be ok.  so these are not default and can be commented out.  and if so desired, can be uncommented at any time.  by commenting them out now, it will eliminate  a possible trouble spot while trouble shooting

---

### Post by raja.genupula on 2011-08-26
> i do not know that they are broken, but the OP (are you one of the same?)

no i am just curious to know , any way thanks man . so you're saying that in his source list the last lines are not commented and these are the causes for his problem , right ?

---

### Post by Enigmapond on 2011-08-26
Looking at what you listed and your mirror site. I would try another software source to see if it's better. Sometimes the best one are not near you. Update Manager/Ubuntu Software and download from. Choose other and let it run a test to see what source is better. Just a shot but it may work.

---

### Post by raja.genupula on 2011-08-26
how **main server** sounds , is this going to be perfect .

---

### Post by jaj540 on 2011-08-27
thanks.... That has fixed the problem...but there was one more broken package ... splashy themes... i also disabled it...now its working fine.... thanks again :)

---

### Post by Enigmapond on 2011-08-27
No problem!

Cheers!

---

