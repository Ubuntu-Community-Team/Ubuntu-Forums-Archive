---
title: "Package lists??"
date: 2010-03-01
forum: General Help
---

### Post by Niloc on 2010-03-01
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/th.archive.ubuntu.com_ubuntu_dists_n_a-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

How can I fix this? I cannot use 'Add /Remove', even a terminal will not seem to find anything!!

Thanks,

Colin

---

### Post by walmartshopper67 on 2010-03-01
hm - what happened leading up to this error? what does your /etc/apt/sources.list look like? (cat /etc/apt/sources.list)?

---

### Post by Niloc on 2010-03-01
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a-updates main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a universe
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a universe
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a-updates universe
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a multiverse
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a multiverse
deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a-updates multiverse
deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a-backports main restricted universe multiverse
# deb-src [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) n/a-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) n/a partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) n/a partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) n/a-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) n/a-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) n/a-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) n/a-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) n/a-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) n/a-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
 
Hope this helps...
Colin

---

### Post by todak on 2010-03-01
What is the [COLOR="Red"]n/a[/COLOR] designation? That seems to be why apt cannot parse the location, as it does not appear to exist in the repositories. Back up a copy of your sources file. Then remove all instances of [COLOR="Red"]n/a[/COLOR] and [COLOR="Red"]n/a-[/COLOR] from the repository URLs and then save the file. Then update as usual.

---

### Post by walmartshopper67 on 2010-03-16
Yikes - i haven't been around here lately, how did you make out Niloc? That n/a thing is pretty weird - I've never seen that before.

---

### Post by soltanis on 2010-03-16
Looks like something messed up. That n/a should designate the codename for your distro release. On my computer, all the n/a's read "karmic".

If you're running Karmic, I suggest you find/replace all n/a with karmic; or if you're running jaunty, then replace them with that string instead.

Hopefully that's the extent of your problems.

---

