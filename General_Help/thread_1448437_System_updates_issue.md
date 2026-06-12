---
title: "System updates issue"
date: 2010-04-06
forum: General Help
---

### Post by wolf_3d on 2010-04-06
For the past month or two, I've been getting this message when using the update manager. Despite the message though, update manager still retrieves updates and installs them like it did today.

The message reads;

W: Failed to fetch [http://repoubuntusoftware.info/dists/karmic/Release.gpg](http://repoubuntusoftware.info/dists/karmic/Release.gpg)  Could not resolve ‘’

W: Failed to fetch [http://repoubuntusoftware.info/dists/karmic/all/i18n/Translation-en_GB.bz2](http://repoubuntusoftware.info/dists/karmic/all/i18n/Translation-en_GB.bz2)  Could not resolve ‘’

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any idea what this is?

---

### Post by snowpine on 2010-04-06
[http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) is NOT an official Ubuntu repository; you must have added it to your software sources for some reason? If you visit the link, you'll see the domain name has expired.

I would recommend going to System->Administration->Software Sources (or 'gksu gedit /etc/apt/sources.list' if you prefer) and removing this obsolete link.

---

### Post by wojox on 2010-04-06
Post your sources.list: 

```
gksudo gedit /etc/apt/sources.list
```

Let's take a look.

---

### Post by wolf_3d on 2010-04-06
Thanks for the replies.

Below is the requested source list. Most of these I have added as they are program specific for programs that I use. Having said that, I'm not sure what the repoubuntusoftware one is.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) karmic cairo-dock

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) karmic main ## Cairo-Dock-PPA
deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) karmic all #Ultimate Edition Repository
deb [http://ppa.launchpad.net/amsn-daily/ppa/ubuntu](http://ppa.launchpad.net/amsn-daily/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) karmic main
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic main
deb [http://debian.keesmeijs.nl/](http://debian.keesmeijs.nl/) karmic-kees main
deb-src [http://debian.keesmeijs.nl/](http://debian.keesmeijs.nl/) karmic-kees main
deb [http://files.lstandish.com/](http://files.lstandish.com/) d2x-xl/
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games

---

### Post by wojox on 2010-04-06
Use that command I posted then comment out # and save:

**deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) karmic all #Ultimate Edition Repository**

That appears to be the offending line. Then run:

```
sudo apt-get update
```

And see what happens.

---

### Post by wolf_3d on 2010-04-07
Yes, thanks for that. It doesn't show the message anymore and seems to function as normal. Marked as solved.

---

