---
title: "Update manager failed to download repository?"
date: 2012-05-28
forum: General Help
---

### Post by bbno3 on 2012-05-28
Ubuntu 12.04

The update manager failed to download repository information saying theres no Internet but i am on the Internet?

W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by MG&amp;TL on 2012-05-28
Can you post the output from a terminal of:

```
cat /etc/apt/sources.list
```

---

### Post by irv on 2012-05-28
This might be that the server the repository is on was down. I have extra repositories setup and once in awhile one is down and I will get this message but will still do an update on the ones that are up and running. If you run the command in a terminal you can copy and paste the exact message you are getting.
```
sudo apt-get update
```
It will ask for you user password and then start the update.

---

### Post by bbno3 on 2012-05-28
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise main restricted independent
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise main restricted independent

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates main restricted independent
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates main restricted independent

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse independent
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse independent

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

_** As for sudo update**_
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by irv on 2012-05-28
In package manager under setting > repository, you have some software sources that are not comparable with your version of ubuntu. Here is a couple of screen shots of my setup in 12.04. I have a lot of extra repositories set under other software sources, but what I would do is uncheck any other sources you have and just try to update with ubuntu software sources and see what happens.
[ATTACH]218853[/ATTACH]        [ATTACH]218854[/ATTACH]

---

### Post by Old_Grey_Wolf on 2012-05-28
I have never seen a sources.list file with "independent" in them. It is in the file in several places. I would edit the sources.list file and remove the word independent from the end of those lines. Then execute sudo apt-get update and sudo apt-get upgrade.

---

### Post by bbno3 on 2012-05-29
@IRV

How do i know what ones to uncheck? I'm still quite new to ubuntu. :confused:

---

### Post by plucky on 2012-05-29
> **bbno3 said:**
> @IRV

How do i know what ones to uncheck? I'm still quite new to ubuntu. :confused:

Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and remove "independent" from all those lines as there is no "Independent" repository ```
 deb http://gg.archive.ubuntu.com/ubuntu/ precise main restricted independent
deb-src http://gg.archive.ubuntu.com/ubuntu/ precise main restricted independent
deb http://gg.archive.ubuntu.com/ubuntu/ precise-updates main restricted independent
deb-src http://gg.archive.ubuntu.com/ubuntu/ precise-updates main restricted independent
```

Then run ```
sudo apt-get update
``` and see if you get the same errors

Good luck

---

### Post by cecilieaux on 2012-05-30
> **MG&TL said:**
> Can you post the output from a terminal of:

```
cat /etc/apt/sources.list
```
The output is:

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted independent
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted independent

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted independent
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted independent

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports restricted main multiverse universe independent
# deb [http://ppa.launchpad.net/scopes-packagers/adult-scopes/ubuntu](http://ppa.launchpad.net/scopes-packagers/adult-scopes/ubuntu) precise main # disabled on upgrade to precise
# deb-src [http://ppa.launchpad.net/scopes-packagers/adult-scopes/ubuntu](http://ppa.launchpad.net/scopes-packagers/adult-scopes/ubuntu) precise main # disabled on upgrade to precise

---

### Post by cecilieaux on 2012-05-30
> **cecilieaux said:**
> The output is:

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted independent
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted independent

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted independent
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted independent

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports restricted main multiverse universe independent
# deb [http://ppa.launchpad.net/scopes-packagers/adult-scopes/ubuntu](http://ppa.launchpad.net/scopes-packagers/adult-scopes/ubuntu) precise main # disabled on upgrade to precise
# deb-src [http://ppa.launchpad.net/scopes-packagers/adult-scopes/ubuntu](http://ppa.launchpad.net/scopes-packagers/adult-scopes/ubuntu) precise main # disabled on upgrade to precise
Oops! I think I jumped in the middle of the wrong thread ... sorrreee!

---

### Post by irv on 2012-05-31
> **Biteryclelync said:**
> mYrdumIivs [http://hoganscarpesitoufficiale.webgarden.com/](http://hoganscarpesitoufficiale.webgarden.com/) qGzlxsCmjc <a href="http://hoganoutletonlinespedizionegratuita.weebly.com/">outlet hogan</a>

What the heck is this?
EDIT: this is post is spam. Trying to sell shoes.

---

### Post by bbno3 on 2012-06-10
SOrry for the delay,

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

Still nothing. :(

---

### Post by bbno3 on 2012-06-10
GUI has loaded up 301 updates? will tell when finished downloading if successful. :)

---

### Post by bbno3 on 2012-06-12
Still says no internet and a red warning is always showing but updates are installable, any ways around the red warning?

---

### Post by Old_Grey_Wolf on 2012-06-12
> **bbno3 said:**
> SOrry for the delay,

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

Still nothing. :(

Did you do what was in post 6 and 8?

---

### Post by Old_Grey_Wolf on 2012-06-12
> **bbno3 said:**
> Still says no internet and a red warning is always showing but updates are installable, any ways around the red warning?

Let us see what the sources.list file looks like now. Post the output from ```
cat /etc/apt/sources.list
```

Let us see what the upgrade errors are now, if any. Post the output from ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bbno3 on 2012-06-13
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse independent
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse independent

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


And

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://gg.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by plucky on 2012-06-13
There are still some lines with **independent** in the line.You need to remove the word **independent** from all the lines.

> deb [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse independent
deb-src [http://gg.archive.ubuntu.com/ubuntu/](http://gg.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse independent

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted independent

Good Luck

---

