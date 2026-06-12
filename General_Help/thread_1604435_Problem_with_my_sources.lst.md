---
title: "Problem with my sources.lst"
date: 2010-10-24
forum: General Help
---

### Post by sofasurfer on 2010-10-24
I installed 10.04 earlier and edited my old sources.lst file by changing "Hardy" references to "lucid". It worked fine. Then I glitched something and had to reinstall again. This time though, after I edited the sources.lst file I get this error when updating...

```

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

```

And when I close out that box I get this message...
```

E: Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list
E: Unable to lock the list directory

```

What did I screw up?

Here is my sources.lst file. If anyone wants to critique it I would be happy to take your advice. I have been using the same list for a long time and it probably has some mistakes somewhere...
```

# deb cdrom:[Ubuntu 10.04_lucid_lynx_ - Release amd64 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 10.04_lucid_lynx _ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/lucid main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted multiverse universe #Added by software-properties

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
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu/ lucid-security main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-security main restricted multiverse universe #Added by software-properties

##added by me according to multimedia how-to
deb http://packages.medibuntu.org/ lucid free non-free
deb-src http://packages.medibuntu.org/ lucid free non-free

##added for google earth
deb http://packages.medibuntu.org/ lucid free non-free
deb-src http://packages.medibuntu.org/ lucid free non-free

##added for wine ppa
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main

##added for firefox-3.5
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
deb http://ppa.launchpad.net/handschuh/ubuntu lucid main

```

---

### Post by howefield on 2010-10-24
Line 1, presumably ;-)

Post the contents here.

```
cat /etc/apt/sources.list
```

---

### Post by ankspo71 on 2010-10-24
Hi,
I don't see what is wrong with line 1, but the first enabled repository  line is wrong.
```
deb http://archive.ubuntu.com/ubuntu/lucid main restricted multiverse universe
```
It should be like this, with a space between ubuntu/ and lucid.
```
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted multiverse universe
```

---

### Post by sofasurfer on 2010-10-24
I had this problem with the space between ubuntu and lucid. I removed the space because I did not know if it should be there. Also, I created a new list from the "Source List Generator"...[http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php)

and I got the same error. So I think its a bug. I think I will reinstall and see what happens.
-------------------------
Here is this result from cat /etc/apt/sources.list.....

# deb cdrom:[Ubuntu 10.04_lucid_lynx_ - Release amd64 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 10.04_lucid_lynx _ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse #Added by software-properties

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
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse #Added by software-properties

##added by me according to multimedia how-to
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

##added for google earth
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

##added for wine ppa
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main

##added for firefox-3.5
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
deb [http://ppa.launchpad.net/handschuh/ubuntu](http://ppa.launchpad.net/handschuh/ubuntu) lucid main

---

### Post by howefield on 2010-10-24
Reinstalling might be a bit of a sledgehammer to crack a nut... 

Edit : sorry disregard, just reread your post again.

---

### Post by Elfy on 2010-10-24
> **howefield said:**
> Reinstalling might be a bit of a sledgehammer to crack a nut... try rebuilding a sources.list from here.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Edit - reread the reread post :)

Do you have any lines at the beginning of the sources list - that is above this line? If you have just what appears to be space - try deleting so the cdrom line is at the top. 

# deb cdrom:[Ubuntu 10.04_lucid_lynx_ - Release amd64 (20090420.1)]/ jaunty main restricted

The '' in line 1 would tend to imply there is something above the cdrom line

---

### Post by sofasurfer on 2010-10-24
It appears that I found the problem. I reinstalled and then tried to download sources using the original sources.lst file. SAME ERROR. Then I had a brain storm. I switched from the U.S. server to the main server and right now my sources are downloading. Must be a glitch at the U.S. server.

---

### Post by sofasurfer on 2010-10-24
Since my last post I have found that I still do not have the answer.
When I tried to load my sources with the sources.list that was included with the distro, I got the error. So I switched from U.S> server to Main server. That tells us that the problem is with the server.

Then I loaded my converted sources.list from my last distro and I got the error with both servers. This tells us that the problem is not with the server.

So I reinstalled and kept the original list that came with the distro and so far all is good. Now I will just rebuild this list slowely and carefully as I need to. Don't know what else to do.

One thing that I did learn was that the old sources.lst is now sources.list. Oops!

---

### Post by ankspo71 on 2010-10-24
Hi,
Why not download a new copy of Ubuntu and install it fresh? 
If you have no CD burner but have a USB drive see these links: 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Upgrade notes for specific older versions of Ubuntu:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
Lucid upgrade notes:
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)
Maverick upgrade notes:
[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

Hope something here helps.

---

