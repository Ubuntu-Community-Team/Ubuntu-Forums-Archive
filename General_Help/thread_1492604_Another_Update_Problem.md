---
title: "Another Update Problem"
date: 2010-05-24
forum: General Help
---

### Post by TurboMaLuM on 2010-05-24
I see others have had this problem and have received help from the forum. 

This is the error: Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

I see that it is usually a problem with the etc/apt/sources.list file. I tried to fix mine from looking at others but cant solve the problem. Will someone who knows more than I look at this and tell me what I need to fix please?

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy multiverse
deb [http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_9.10/](http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_9.10/) ./

---

### Post by -humanaut- on 2010-05-25
> 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy multiverse
deb [http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_9.10/](http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_9.10/) ./

Try commenting out those three with a # I highly suspect edgy repos are no longer there and the opensuse url doesn't look right.

---

### Post by TurboMaLuM on 2010-05-25
Thanks for the suggestion, I did that and it still gave me this error:

Failed to fetch [http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Not  sure...what else do you think could be the problem?

I don't think I even mentioned, and not sure if it matters, but I'm using 10.04 Ubuntu

---

### Post by mgol on 2010-05-25
> **TurboMaLuM said:**
> Failed to fetch [http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found


You can still have some entries in separate files lying in /etc/apt/sources.list.d/ directory. Check if it's empty; if not, post here contents of files there.

---

### Post by TurboMaLuM on 2010-05-25
/etc/apt/sources.list.d/compiz-ppa-lucid.list
/etc/apt/sources.list.d/compiz-ppa-lucid.list.save
/etc/apt/sources.list.d/coolwanglu-scanmem.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/moovida-packagers-ppa-lucid.list
/etc/apt/sources.list.d/moovida-packagers-ppa-lucid.list.save
/etc/apt/sources.list.d/playdeb.list
/etc/apt/sources.list.d/playdeb.list.save
/etc/apt/sources.list.d/ubuntu-tweak-stable.list
/etc/apt/sources.list.d/ubuntu-tweak-stable.list.save

What doesn't look good? Should I enabled those 3 I commented out earlier or leave them out?

---

### Post by mgol on 2010-05-25
> **TurboMaLuM said:**
> /etc/apt/sources.list.d/compiz-ppa-lucid.list
/etc/apt/sources.list.d/compiz-ppa-lucid.list.save
/etc/apt/sources.list.d/coolwanglu-scanmem.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/moovida-packagers-ppa-lucid.list
/etc/apt/sources.list.d/moovida-packagers-ppa-lucid.list.save
/etc/apt/sources.list.d/playdeb.list
/etc/apt/sources.list.d/playdeb.list.save
/etc/apt/sources.list.d/ubuntu-tweak-stable.list
/etc/apt/sources.list.d/ubuntu-tweak-stable.list.save

What doesn't look good? Should I enabled those 3 I commented out earlier or leave them out?
You have a lot of additional stuff added there; do You recognize adding those particular ones?

Those 3 deleted ones were definitely wrong - two were for archaic Edgy and one for OpenSUSE; I don't know how did You get them there.

If You don't recognize some of these additional repositories, it may be better to delete their files (or at least move them to some backup directory).

Error is definitely about moovida package, so this is the first thing to remove. I found this PPA:
[https://launchpad.net/~moovida-packagers/+archive/ppa](https://launchpad.net/~moovida-packagers/+archive/ppa)
and it doesn't have its Lucid version. No wonder it doesn't work...

---

### Post by -humanaut- on 2010-05-25
> **TurboMaLuM said:**
> /etc/apt/sources.list.d/compiz-ppa-lucid.list
/etc/apt/sources.list.d/compiz-ppa-lucid.list.save
/etc/apt/sources.list.d/coolwanglu-scanmem.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/moovida-packagers-ppa-lucid.list
/etc/apt/sources.list.d/moovida-packagers-ppa-lucid.list.save
/etc/apt/sources.list.d/playdeb.list
/etc/apt/sources.list.d/playdeb.list.save
/etc/apt/sources.list.d/ubuntu-tweak-stable.list
/etc/apt/sources.list.d/ubuntu-tweak-stable.list.save

What doesn't look good? Should I enabled those 3 I commented out earlier or leave them out?

You have a ton of stuff try commenting out everything expect the essential repositories and run 

sudo apt-get clean && sudo apt-get update

you should be more careful about adding repos can cause dependency hell and break updates.

---

