---
title: "Repository Problems"
date: 2012-05-27
forum: General Help
---

### Post by randyscott101 on 2012-05-27
Hi guys,
I'm new here so bare with me. There is something wrong with my repositories. I keep getting an error whenever I try to run  Synaptic or the Update Manager.  This is what error message I keep getting:
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Please help me.
Randy

---

### Post by drs305 on 2012-05-27
randyscott101,

Welcome to the Ubuntu Forums. :-)

There is something wrong with your respository listings in the /etc/apt/sources.list file. You can open it with a text editor as root:
```
gksu gedit +60 /etc/apt/sources.list &
sudo apt-get update
```
Either place a # symbol at the start of the line to make the system ignore it, or copy it and post it here and we can take a look (the line or the entire file).

Once you fix the entry, save the file and run the second command above to see if your repository index now works.

---

### Post by cecilieaux on 2012-05-27
> **drs305 said:**
> randyscott101,

Welcome to the Ubuntu Forums. :-)

There is something wrong with your respository listings in the /etc/apt/sources.list file. You can open it with a text editor as root:
```
gksu gedit +60 /etc/apt/sources.list &
sudo apt-get update
```
Either place a # symbol at the start of the line to make the system ignore it, or copy it and post it here and we can take a look (the line or the entire file).

Once you fix the entry, save the file and run the second command above to see if your repository index now works.
I tried your solution for a similar problem. No go. My error message from update is:

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/Release](http://archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by codingman on 2012-05-27
> **cecilieaux said:**
> I tried your solution for a similar problem. No go. My error message from update is:

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/Release](http://archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
was that the output for sudo apt-get update?
If so you need to do:
```
cat /etc/apt/sources.list
```
and then go post the output here

---

### Post by drs305 on 2012-05-27
In case the OP also doesn't fix things, try opening Software Sources (via Synaptic > Settings, Repositories; Update-Manager > Settings; or Ubuntu Software Center: Edit, Software Sources.

Go to the Ubuntu Software tab and untick anything that is selected. Wait a few seconds and then reselect them. This will remove/refresh any corrupted package list.

Reload or "sudo apt-get update".

---

### Post by randyscott101 on 2012-05-28
Thanks guys, it worked. I was able to update again.
Thanks again.
randy.

---

### Post by cecilieaux on 2012-05-30
> **codingman said:**
> was that the output for sudo apt-get update?
If so you need to do:
```
cat /etc/apt/sources.list
```
and then go post the output here
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
> **drs305 said:**
> In case the OP also doesn't fix things, try opening Software Sources (via Synaptic > Settings, Repositories; Update-Manager > Settings; or Ubuntu Software Center: Edit, Software Sources.

Go to the Ubuntu Software tab and untick anything that is selected. Wait a few seconds and then reselect them. This will remove/refresh any corrupted package list.

Reload or "sudo apt-get update".
Unchecked ubuntu sources and reloaded and I got:


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'independent/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'independent/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by drs305 on 2012-05-31
> **cecilieaux said:**
> The output is:

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted **[COLOR="Red"]independent[/COLOR]**
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted **[COLOR="Red"]independent[/COLOR]**

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted **[COLOR="Red"]independent[/COLOR]**
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted **[COLOR="Red"]independent[/COLOR]**

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
**[COLOR="Red"]deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner[/COLOR]**

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


I'm not familiar with "independent", so you might try removing it from each of the highlighted lines. Also, the "maverick" refererence is going to give you problems eventually, as its repositories either have been or will shortly be moved.

---

### Post by cecilieaux on 2012-06-03
Thanks, drs305. It worked!!!!

---

