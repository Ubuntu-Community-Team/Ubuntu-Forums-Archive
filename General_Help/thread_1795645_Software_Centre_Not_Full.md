---
title: "Software Centre Not Full"
date: 2011-07-03
forum: General Help
---

### Post by Quarkrad on 2011-07-03
Newbie - just done a clean install of 10.10. Building up system and added a number of ppa's to my 'sources list' as well as the main list (Canonical supported Open Source Software (main), universe, multiuniverse, etc). I wanted to upgrade to Firefox 5 but when I looked in Software Centre, Get Software, Internet, Web Browsers the list is empty.  I guess my Sources List is way off.  Here is my **/etc/apt/sources.list** file

[B]# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick restricted universe main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates restricted universe main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

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

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security restricted universe main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick non-free #VirtualBox
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe[/B]

What should I do to populate my software Centre with at least the basic software set?

---

### Post by dino99 on 2011-07-03
open synaptic and check the repo activation

---

### Post by plucky on 2011-07-03
> What should I do to populate my software Centre with at least the basic software set?


From a terminal ```
sudo apt-get update
```

Good Luck

---

### Post by Quarkrad on 2011-07-03
I have done a apt-get update as well as a apt-get upgrade.  Also, I'm not sure how to **check the repo activation**.  Did a bit of googling on this but still not sure where it is in Synaptic.

---

### Post by dino99 on 2011-07-03
> **Quarkrad said:**
> I have done a apt-get update as well as a apt-get upgrade.  Also, I'm not sure how to **check the repo activation**.  Did a bit of googling on this but still not sure where it is in Synaptic.

you might see tabs and checkboxes

but if you never heard about synaptic: sudo synaptic

---

### Post by plucky on 2011-07-03
Did you create the list yourself or was it created during the install?

I don't have a Maverick list,but my Natty list looks like ```
cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty universe
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ natty-updates multiverse

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
deb http://archive.canonical.com/ubuntu natty partner

deb http://gb.archive.ubuntu.com/ubuntu/ natty-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ natty-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ natty-security multiverse
deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository

```

Notice the / after the **ubuntu** and before the **natty**

Could that be your problem?

Good Luck

---

### Post by Quarkrad on 2011-07-03
Natty is not in the picture. This is the fist time this has happened - for various reasons I've done a clean install of 10.10 many times  this is the first time I've had an issue with Software Centre/Source List. I have not created the list -it was compiled from a Clean Install, sudo apt-get update and installing of various apps.

---

### Post by plucky on 2011-07-03
> **Quarkrad said:**
> Natty is not in the picture. This is the fist time this has happened - for various reasons I've done a clean install of 10.10 many times  this is the first time I've had an issue with Software Centre/Source List. I have not created the list -it was compiled from a Clean Install, sudo apt-get update and installing of various apps.

What I am saying is that maybe you could make a copy of the file and then edit the copy and add the / after ubuntu on each line and see if it then loads the lists from the repositories.
If that doesn't work,you still have the original copy of the sources.list file to revert back.

Good Luck

---

### Post by Quarkrad on 2011-07-04
Hasn't worked - I've now tried sources from a number of places - including the default 10.10 sources list.  Each time I try a new list I enter **sudo apt-get update** in terminal before looking at the software Centre.  I can install software via the terminal but only those I know of.  There is still no browsers listed in Software Centre - no Rsync, etc. etc.

---

### Post by wildmanne39 on 2011-07-04
> **Quarkrad said:**
> Hasn't worked - I've now tried sources from a number of places - including the default 10.10 sources list.  Each time I try a new list I enter **sudo apt-get update** in terminal before looking at the software Centre.  I can install software via the terminal but only those I know of.  There is still no browsers listed in Software Centre - no Rsync, etc. etc.Hi, you can use these two commands together to clear out the list and rebuild it with the original list.
```
sudo rm /var/lib/apt/lists/* -vf

```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by Quarkrad on 2011-07-04
Made no difference - I got these errors at the end of sudo apt-get update but I do not think they should effect the population of Software Centre

[B]W: GPG error: [http://deb.opera.com](http://deb.opera.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8
W: Failed to fetch [http://debian.scribus.net/debian/dists/testing/Release](http://debian.scribus.net/debian/dists/testing/Release)  Unable to find expected entry  non-free/binary-amd64/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]


I haven't been through every option in Software Centre but for example under Get Software:

Sound & Video   3 Fluendo options (which I think are 'pay for') 
Office  Empty
Internet/File Sharing/Chat/Mail/Web Browsers/All 0 - Empty
All Science & Engineering - Empty

---

### Post by hawthornso23 on 2011-07-04
Here for comparison purposes are the contents of /etc/apt/sources.list on my maverick machine ... which was upgraded from Lucid upgraded from Jaunty upgraded from Intrepid and which is running just fine with a fully populated Ubuntu software center.

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse

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
deb http://archive.canonical.com/ubuntu maverick partner

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb http://archive.ubuntu.com/ubuntu maverick-backports restricted main multiverse universe

## Manual additions.
## Tor repository for Tor onion routing software.
# deb http://deb.torproject.org/torproject.org maverick main # disabled on upgrade to maverick
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository

```Plucky: - note there is no trailing / after ubuntu. Looks like this is normal for maverick.

---

### Post by hawthornso23 on 2011-07-04
Suggestion: try reinstalling software-center

---

### Post by Quarkrad on 2011-07-04
Thanks - just used your list and sudo apt-get update.  No difference!  I will fnd out how and reinstall.

---

### Post by Quarkrad on 2011-07-04
That did it - un-installed and re-intalled via Synaptic.  Many thanks - a happy bunny here!

---

