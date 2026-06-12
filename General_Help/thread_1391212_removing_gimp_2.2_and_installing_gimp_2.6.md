---
title: "removing gimp 2.2 and installing gimp 2.6"
date: 2010-01-26
forum: General Help
---

### Post by angry ogre on 2010-01-26
i  want to upgrade to gimp 2.6 so i uninstalled 2.2 and installed 2.6 via synaptic and it wont work. the launcher quits after 10 secs or so and when i run "gimp" in the terminal 2.2 still runs. can someone tell me how to remove 2.2 completely and install 2.6, any help is appreciated,btw i upgraded from jaunty to karmic last night but this issue has been going on for some time now.

---

### Post by unmole on 2010-01-26
Do ```
aptitude purge gimp
```to remove gimp completely, relod package information and then install gimp.

---

### Post by angry ogre on 2010-01-26
how do i reload pkg information?

---

### Post by snowpine on 2010-01-26
Gimp 2.6 has been standard since Intrepid. Please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by angry ogre on 2010-01-26
brandon@brandon-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse

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

# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope disabled on upgrade to karmic
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic

---

### Post by snowpine on 2010-01-26
Your software sources look good. No idea why you're stuck on Gimp 2.2. :(

---

### Post by 3rdalbum on 2010-01-26
> **snowpine said:**
> Your software sources look good.

Why are there some Jaunty and some Karmic entries?

Remove the contents of the /etc/apt/sources.list file, and then use the System > Administration > Software Sources program to enable all your repositories. Then you should have a proper sources.list.

If you have manually-installed Gimp 2.2 in the past, it will probably be sitting in /usr/local/bin which will take precedence over any later versions in /usr/bin. Remove Gimp from /usr/local/bin if it is there.

---

### Post by angry ogre on 2010-01-27
that works like a charm,thank you.

---

