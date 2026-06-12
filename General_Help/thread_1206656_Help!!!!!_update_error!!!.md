---
title: "Help!!!!! update error!!!"
date: 2009-07-07
forum: General Help
---

### Post by Blacklightbulb on 2009-07-07
When I try to update repos 
```

sudo apt-get update
```

I get this error: 

```
W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/jaunty/Release  Unable to find expected entry  not/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I'm stuck. Help:confused:

---

### Post by philinux on 2009-07-07
Have a look in your software sources. Could be you added the wrong source archive.

---

### Post by Blacklightbulb on 2009-07-07
Dunno seams ok. What should I look for in the system software sources?:confused:

---

### Post by wirelessmonkey on 2009-07-07
The line in your software sources for that repo should look like this:

```

deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main 

```

Double check that this is the case, then refresh.

---

### Post by Blacklightbulb on 2009-07-07
Double check. No luck. Identical.

---

### Post by Blacklightbulb on 2009-07-07
Is the error on my side or could it be on the server side. I already connected and reupdated on three different servers: Italy, US and Germany. Still no luck.

---

### Post by philinux on 2009-07-07
Post your sources list.

```
cat /etc/apt/sources.list
```

Don't forget to put code tags around it.

---

### Post by Blacklightbulb on 2009-07-07
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.intergenia.de/ubuntu/ jaunty multiverse restricted universe main
deb-src http://ubuntu.intergenia.de/ubuntu/ jaunty multiverse restricted universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.intergenia.de/ubuntu/ jaunty-updates multiverse restricted universe main
deb-src http://ubuntu.intergenia.de/ubuntu/ jaunty-updates multiverse restricted universe main #Added by software-properties

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
## N.B. software from this repository maydeb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mt.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://mt.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://ubuntu.intergenia.de/ubuntu/ jaunty-security multiverse restricted universe main
deb-src http://ubuntu.intergenia.de/ubuntu/ jaunty-security multiverse restricted universe main #Added by software-properties
deb http://ubuntu.intergenia.de/ubuntu/ jaunty-proposed multiverse restricted universe main
deb-src http://ubuntu.intergenia.de/ubuntu/ jaunty-proposed multiverse restricted universe main #Added by software-properties
deb http://ubuntu.intergenia.de/ubuntu/ jaunty-backports multiverse restricted universe main
deb-src http://ubuntu.intergenia.de/ubuntu/ jaunty-backports multiverse restricted universe main #Added by software-properties
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main


deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main


```

As clearly seen I'm connected to a german server right now.

---

### Post by philinux on 2009-07-07
```
## N.B. software from this repository maydeb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main **[COLOR="Red"]not have been tested as[/COLOR]**

```

Error here.

---

### Post by Blacklightbulb on 2009-07-07
So what now? I gedited the file (where it says uncomment the following ......) but still it didn't work:confused:?!

---

### Post by Blacklightbulb on 2009-07-07
Ok gedited again and no errors!!!!!!!

Thanks Guys!!!!!!!!!:lolflag:

---

