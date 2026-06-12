---
title: "Error while searching for updates"
date: 2009-07-14
forum: General Help
---

### Post by orion1315 on 2009-07-14
W: GPG error: [http://repository.cairo-dock.org]("http://repository.cairo-dock.org/") jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877
W: GPG error: [http://wine.budgetdedicated.com]("http://wine.budgetdedicated.com/") jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

This is im sure, a HUGE problem because if i cant get updates, well, thats bad.
It starts looking for updates and it gets to like 50 or so then it shows the error and goes back to the blank update thing.

Please help :sad: new to ubuntu here.

---

### Post by mikewhatever on 2009-07-14
These errors should not prevent you getting updates. They only mean that two third party repositories aren't authenticated. You should probably post you sources list for review. Use the following command,
**gedit /etc/apt/sources.list**, then copy the contents of the file and post here.

---

### Post by philinux on 2009-07-14
> **mikewhatever said:**
> These errors should not prevent you getting updates. They only mean that two third party repositories aren't authenticated. You should probably post you sources list for review. Use the following command,
**gedit /etc/apt/sources.list**, then copy the contents of the file and post here.

snip

---

### Post by turinglabs on 2009-07-14
Any legitimate third-party repository will make the GPG keys available for importing into your local configurstion. For exmple, the wine repo page you list has a link to instructions here:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Just scroll down to "Trusting the WineHQ APT Repository and installing Wine:"

---

### Post by michy99 on 2009-07-14
Try this in terminal:```
gpg --keyserver subkeys.pgp.net --recv 1392A97E41317877
gpg --export --armor 1392A97E41317877 | sudo apt-key add -
gpg --keyserver subkeys.pgp.net --recv 58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -
sudo apt-get update
```

---

### Post by orion1315 on 2009-07-14
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"

there you are :)
edit:nvm thank you fixed, if i ran that stuff in terminal when i alrdy had the wine key or whatever, will it make any difrence? and does this mean it will update cairo and wine automaticly with the update manager?

---

