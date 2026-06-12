---
title: "Repository error, file not gzipped?"
date: 2006-06-27
forum: General Help
---

### Post by Carl Foxmarten on 2006-06-27
I'm not entirely new to Linux, I've been using it for at least a year and Ubuntu 5.10 for about six months now and prefer it to SuSE (one of my previous Linux distros).

My current problem (which is more of an annoyance so far) is that a particular repository isn't working properly. When I update the package information it gives me an error:
> [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

I had been attempting to install Xgl, but it wouldn't let me because a package required by most packages (mostly the Xgl server) needed to be a certain version when it wasn't available, and I think that this is my problem.

My sources.list file is as follows:

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu breezy-updates main universe
deb-src http://ca.archive.ubuntu.com/ubuntu breezy-updates main universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb-src http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe

deb http://security.ubuntu.com/ubuntu breezy-security main
deb-src http://security.ubuntu.com/ubuntu breezy-security main

deb http://security.ubuntu.com/ubuntu breezy-security universe
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy main restricted
deb http://www.beerorkid.com/compiz/ dapper main
deb http://wine.budgetdedicated.com/apt breezy main
deb http://xgl.compiz.info/ dapper main aiglx
#deb http://xgl.compiz.info/ dapper main

```

I do know quite a bit about working on Linux after using various stripped-down distros, so you don't have to spare the language.

And if you could point me to a list of all the official repositories so I know if some of my list are invalid, that would be great!

Thanks for any help you can give me!
Carl.

---

