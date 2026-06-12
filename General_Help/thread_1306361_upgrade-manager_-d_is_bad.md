---
title: "upgrade-manager -d is bad"
date: 2009-10-30
forum: General Help
---

### Post by running_rabbit07 on 2009-10-30
After reading this [thread]("http://ubuntuforums.org/showthread.php?p=8196930#post8196930") I would love to know how to undo this command, ```
sudo upgrade-manager -d
``` Basically, people need to know that this is the command to upgrade to the development release and will show a new upgrade is available as soon as the devs make the first 10.04 image. 

How do we undo this command if we have already used it?

---

### Post by grandtoubab on 2009-10-30
I don't see the point as the next testing 10.04 is not open!

If you are worrying check your apt-list 
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

Should have only Karmic references in not commented lines
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Edubuntu 8.10 _Intrepid Ibex_ - Release i386 Binary-1 (20081027.1)]/ intrepid main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

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
# deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe

# deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main
# deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main
# deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) etch/volatile main contrib non-free
# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
# deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
# deb [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) jaunty main
# deb-src [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) jaunty main

---

### Post by jocko on 2009-10-30
> **running_rabbit07 said:**
> After reading this [thread]("http://ubuntuforums.org/showthread.php?p=8196930#post8196930") I would love to know how to undo this command, ```
sudo upgrade-manager -d
``` Basically, people need to know that this is the command to upgrade to the development release and will show a new upgrade is available as soon as the devs make the first 10.04 image. 

How do we undo this command if we have already used it?
"update-manager -d" is NOT bad. It does exactly what it is intended to do. But some users seems to be sloppy with reading the info they get when they run the command.

When update-manager is started with the -d switch it will inform you that a new version is available, even when this new version is still in development. And it will say which version it will upgrade to and let you cancel *before* any changes are made. 
To avoid this, why don't you just start the upgrade manager from the starter in the menu (System-->Administration-->Update manager)

---

### Post by running_rabbit07 on 2009-10-30
> **jocko said:**
> "upgrade-manager -d" is NOT bad. It does exactly what it is intended to do. But some users seems to be sloppy with reading the info they get when they run the command.

When upgrade-manager is started with the -d switch it will inform you that a new version is available, even when this new version is still in development. And it will say which version it will upgrade to and let you cancel *before* any changes are made. 
To avoid this, why don't you just start the upgrade manager from the starter in the menu (System-->Administration-->Upgrade manager)

Apperently you didn't read the link above. I don't have the problem, but there are many who will start seeing these issues come up. There were people using that command yesterday because the upgrade was not there in their Upgrade Manager.

BTW, thanks for implying that I am sloppy. I did not upgrade with that method nor was I the one giving that command to every newb that said they couldn't get the upgrade to show up in the manager.

Lets try to help people.

---

### Post by jocko on 2009-11-03
> **running_rabbit07 said:**
> Apperently you didn't read the link above. I don't have the problem, but there are many who will start seeing these issues come up. There were people using that command yesterday because the upgrade was not there in their Upgrade Manager.

BTW, thanks for implying that I am sloppy. I did not upgrade with that method nor was I the one giving that command to every newb that said they couldn't get the upgrade to show up in the manager.

Lets try to help people.
I did read the link, and I totally agree that people should never tell other users to run update-manager with the -d switch if all they want is to update to the latest (stable) release. But it's not the fault of update-manager that people break their installs by taking bad advice. The fault is with the people giving the bad advice, and the users that run the command without reading the messages they get from it.

And as far as I understand, there is no way of undoing an upgrade after the actual install process has started, but with the update-manager there are plenty of time to back out before any permanent changes are made, at least for an observant user.

IMO, the best way to help is probably to correct people that give bad advice and telling them how to do things correctly, instead of flooding the forum with threads like "upgrade-manager -d" is bad, "rm -rf" is bad, "formatting the hard drive is bad" *etc*. In the end you'll end up with a long list of commands that are "bad" bacause they can be used to do things that can result in loss of data if you tell them to by adding the (im)proper switches.

---

