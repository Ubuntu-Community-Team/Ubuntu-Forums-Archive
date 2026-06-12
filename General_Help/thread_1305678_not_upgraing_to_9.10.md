---
title: "not upgraing to 9.10"
date: 2009-10-30
forum: General Help
---

### Post by krishna1650 on 2009-10-30
hello all, for last two hours i am trying to upgrade from 9.04 to 9.10. but update manager is not showing any option to upgrade the system. so please tell me how to upgrade it.

thanks.

---

### Post by asaz989 on 2009-10-30
By default, you should see the new update available after clicking (in update-manager) the "Check" button.

If that doesn't work, first try (at the command line)
```
sudo apt-get update
```

Then run update-manager again. If it still doesn't give you a button at the top to upgrade to 9.10, close update manager and run the following:

```
update-manager -d
```

That should open a new Update Manager window with the "Upgrade to Ubuntu 9.10" button. If that doesn't work.... :-k I don't know.

---

### Post by jmszr on 2009-10-30
krishna1650,

You might go to System > Administration > Software Sources > Updates and under "Release upgrade" check to make sure it's set to "Normal releases".

Here are a couple of links that you may find useful: [http://ubuntu-tutorials.com/2009/10/28/how-to-upgrade-to-ubuntu-9-10-karmic-koala/](http://ubuntu-tutorials.com/2009/10/28/how-to-upgrade-to-ubuntu-9-10-karmic-koala/) and: [http://www.ubuntugeek.com/howto-upgrade-ubuntu-9-04-jaunty-to-9-10-karmic-desktopserver.html](http://www.ubuntugeek.com/howto-upgrade-ubuntu-9-04-jaunty-to-9-10-karmic-desktopserver.html) .

Hope that helps.

---

### Post by krishna1650 on 2009-10-30
> **asaz989 said:**
> By default, you should see the new update available after clicking (in update-manager) the "Check" button.

If that doesn't work, first try (at the command line)
```
sudo apt-get update
```

Then run update-manager again. If it still doesn't give you a button at the top to upgrade to 9.10, close update manager and run the following:

```
update-manager -d
```

That should open a new Update Manager window with the "Upgrade to Ubuntu 9.10" button. If that doesn't work.... :-k I don't know.

thanks for the reply. whenever i am use "check" in update manager, i get this following error.
------

W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
---------

i need some further help.

---

### Post by grandtoubab on 2009-10-30
[http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

maybe you have to change your software sources (change the server)  and run again sudo apt-get update
then continue the standard process

---

### Post by krishna1650 on 2009-10-30
> **grandtoubab said:**
> [http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

maybe you have to change your software sources (change the server)  and run again sudo apt-get update
then continue the standard process

it seems like, there is some problem in repository configuration and key. can anyone tell, how to set default repository with it's key.

---

### Post by grandtoubab on 2009-10-30
Below my file:

[B]desktop:~$ cat /etc/apt/sources.list
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

[/B]Refer to[URL="http://www.debian.org/doc/manuals/apt-howto/index.fr.html"]
[/URL][B][_http://www.debian.org/doc/manuals/apt-howto/_]("http://www.debian.org/doc/manuals/apt-howto/")

[/B]my keys:
[B]sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/0C5A2783 2006-11-23
uid                  Medibuntu Packaging Team <admin@lists.medibuntu.org>
uid                  The Medibuntu Team <medibuntu@sos-sts.com>
sub   2048g/16C7105A 2006-11-23

pub   1024R/881574DE 2009-03-10
uid                  Launchpad PPA for Bisigi

pub   1024R/7EBC211F 2009-01-22
uid                  Launchpad PPA for Ubuntu Mozilla Security Team

pub   1024D/6A423791 2006-09-26 [expiré: 2009-09-25]
uid                  Opera Software Archive Automatic Signing Key <hostmaster@opera.com>

pub   1024D/BBE55AB3 2007-03-31 [expire: 2010-03-30]
uid                  Debian-Volatile Archive Automatic Signing Key (4.0/etch)
sub   2048g/36CA98F3 2007-03-31 [expire: 2010-03-30]
[/B]

refer to 
[http://www.annodex.net/cgi-bin/man/man2html?apt-key+8](http://www.annodex.net/cgi-bin/man/man2html?apt-key+8)

---

### Post by slakkie on 2009-10-30
> **asaz989 said:**
> By default, you should see the new update available after clicking (in update-manager) the "Check" button.

If that doesn't work, first try (at the command line)
```
sudo apt-get update
```

Then run update-manager again. If it still doesn't give you a button at the top to upgrade to 9.10, close update manager and run the following:

```
update-manager -d
```

That should open a new Update Manager window with the "Upgrade to Ubuntu 9.10" button. If that doesn't work.... :-k I don't know.

update-manager -d is to upgrade to a development release. PLEASE DO NOT ADVISE PEOPLE TO USE THIS FOR NORMAL UPGRADES. If someone runs this on Karmic in about 3 weeks he will install a development release of Ubuntu (Lucid) and that could cause serious issues!

---

