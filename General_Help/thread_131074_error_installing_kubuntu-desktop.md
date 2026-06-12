---
title: "error installing kubuntu-desktop"
date: 2006-02-15
forum: General Help
---

### Post by shams2 on 2006-02-15
hi,
i run the apt-get install kubuntu-desktop it was working fine and nearly to complete the downloads of necessary packages, but today when i start to run the apt-get update this was the only error:
Get:19 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [Working]                                                        4916B/s 0s
gzip: stdin: not in gzip format
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
and then when i run the apt-get install kubuntu-desktop this is the error:
# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: konq-plugins but it is not going to be installed
E: Broken packages
then i run apt-get -f install kubuntu-desktop and got the same error, pleas help me?

---

### Post by oakz on 2006-02-15
try first running

$ sudo apt-get -f update

...to fix your apt state and remove broken dependencies. Then try to install kubuntu-desktop again. If that doesn't work post the error to this thread.

---

### Post by aysiu on 2006-02-15
Post the output of this command: ```
cat /etc/apt/sources.list
```

---

### Post by shams2 on 2006-02-15
thanks for replies i run the apt-get -f update and this was the error:
Get:20 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [Working]                                                        4553B/s 0s
gzip: stdin: not in gzip format
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 185kB in 36s (5034B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/pk.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/pk.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

then i run the apt-get install kubunt-desktop and got the same dependency error, this is my sources.list:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
## Uncomment the following two lines to fetch updated software from the network
 deb file:/store/ubuntu/ updates/
 deb [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy main restricted
#deb-src [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy universe
#deb-src [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://pk.archive.ubuntu.com/ubuntu](http://pk.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by aysiu on 2006-02-15
Can you try following the instructions in the first link of my signature?

---

