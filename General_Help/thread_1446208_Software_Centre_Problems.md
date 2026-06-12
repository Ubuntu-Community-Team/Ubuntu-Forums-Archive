---
title: "Software Centre Problems"
date: 2010-04-03
forum: General Help
---

### Post by Zackykins on 2010-04-03
Hey 
I recently installed Ubuntu 9.10 onto a laptop with no experience with using Linux or anything like that, proper newbie to this. Anyhows, tried to look for some free software. When I start it up, it says theres 2000 and something things I can download, but when I click on a category, it says there aren't any. I searched the threads and forund one telling me to type 'sudo apt-get install --reinstall software-center' into the terminal, this just returned 'E: Type ‘hpad.net/globalmenu-team/ppa/ubuntu’ is not known on line 49 in source list /etc/apt/sources.list
E: The list of sources could not be read.'

I'd rather not have to reinstall Ubunto because already had to before and I've spent ages making it look nice and Macish with the nice AWN thingy :)

Any Ideas?

Thankyou Very MUuch :)

---

### Post by Naitsirhc Hsem on 2010-04-03
have you updated since the install?

---

### Post by Rocket2DMn on 2010-04-03
Can you please post your sources.list file here, it looks like there is an invalid entry in it.  We can get it cleaned up for you.

You can either navigate to */etc/apt* in the file browser and open *sources.list* or you can run in terminal:
```
cat /etc/apt/sources.list
```

Copy and paste the output here.

---

### Post by Zackykins on 2010-04-04
Hey and Happy Easter ;)

Yeah I did install some updates when I installed Ubuntu :)

Cheers for the replies too guys :)

This is what comes up:

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
hpad.net/globalmenu-team/ppa/ubuntu karmic main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) karmic main

I tried to upload it but wouldn't let me :S

There are two, sources.list and sources.list.save if that makes any difference?

Thanks a lot :)

---

### Post by Zackykins on 2010-04-04
Hey just fixed it I think, deleted the offending line 49:
hpad.net/globalmenu-team/ppa/ubuntu karmic m

and all seems to be doing fine :)
But if there's anything else I needa do please help?

Thanks :)

---

### Post by Rocket2DMn on 2010-04-04
Yup, that would be the problem you had - glad you got it fixed.  You should be able to update/upgrade as well as install new software now.

Happy Easter to you as well :)

---

