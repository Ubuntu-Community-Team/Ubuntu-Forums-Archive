---
title: "E:Malformed line 53 in source list"
date: 2012-10-10
forum: General Help
---

### Post by hangepe on 2012-10-10
Hi,
After trying to install the Adobe Reader, I now get the following exception:

E:Malformed line 53 in source list /etc/apt/ sources.list (dist parse).
I'm on 12.04 - Precise Pangolin

Here's the output from the source list:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository

deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

I would appreciate some help with this.

Thanks.

//HP.

---

### Post by Cheesemill on 2012-10-10
You need to delete lines 53 and 54 as they don't have the correct syntax (I've highlighted them in red below).
 
# See [[COLOR=#000000]http://help.ubuntu.com/community/UpgradeNotes[/COLOR]]("http://help.ubuntu.com/community/UpgradeNotes") for how to upgrade to
# newer versions of the distribution.

deb [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise main restricted
deb-src [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise-updates main restricted
deb-src [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise universe
deb-src [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise universe
deb [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise-updates universe
deb-src [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise multiverse
deb-src [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise multiverse
deb [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise-updates multiverse
deb-src [[COLOR=#000000]http://dk.archive.ubuntu.com/ubuntu/[/COLOR]]("http://dk.archive.ubuntu.com/ubuntu/") precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [[COLOR=#000000]http://archive.canonical.com/ubuntu[/COLOR]]("http://archive.canonical.com/ubuntu") precise partner
deb-src [[COLOR=#000000]http://archive.canonical.com/ubuntu[/COLOR]]("http://archive.canonical.com/ubuntu") precise partner

deb [[COLOR=#000000]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") precise-security main restricted
deb-src [[COLOR=#000000]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") precise-security main restricted
deb [[COLOR=#000000]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") precise-security universe
deb-src [[COLOR=#000000]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") precise-security universe
deb [[COLOR=#000000]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") precise-security multiverse
deb-src [[COLOR=#000000]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") precise-security multiverse
deb [[COLOR=#000000]http://extras.ubuntu.com/ubuntu[/COLOR]]("http://extras.ubuntu.com/ubuntu") precise main #Third party developers repository

**[COLOR=red]deb [/COLOR]**[**[COLOR=red]http://archive.canonical.com/[/COLOR]**]("http://archive.canonical.com/")[B][COLOR=red] partner
deb-src [/COLOR][/B][**[COLOR=red]http://archive.canonical.com/[/COLOR]**]("http://archive.canonical.com/")[B][COLOR=red] partner
[/COLOR][/B]deb [[COLOR=#000000]http://archive.canonical.com/[/COLOR]]("http://archive.canonical.com/") precise partner
deb-src [[COLOR=#000000]http://archive.canonical.com/[/COLOR]]("http://archive.canonical.com/") precise partner

---

### Post by hangepe on 2012-10-10
Thank you.

It seems to have done the trick.

---

### Post by SlugSlug on 2012-10-10
you can hash out (#) all the deb-src entries if you don't download the sources?

This will speed up apt-get update

---

