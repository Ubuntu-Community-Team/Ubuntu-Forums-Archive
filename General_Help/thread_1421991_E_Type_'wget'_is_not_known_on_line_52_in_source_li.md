---
title: "E: Type 'wget' is not known on line 52 in source list /etc/apt/sources.list"
date: 2010-03-04
forum: General Help
---

### Post by tylerjfisher on 2010-03-04
I was trying to install the medibuntu packages through the terminal via the following code ```
[B]sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update[/B]
```Upon doing so, I received this message in the terminal. Somethings up! 
```
E: Type 'wget' is not known on line 52 in source list /etc/apt/sources.list

```[COLOR=Sienna]

[COLOR=Black]I'd GREATLY appreciate some help, I'm really new to Ubuntu I've just migrated from Win7x64. Thanks in advance! 

Tyler J. Fisher[/COLOR]


[U][COLOR=Black]Here's my sources.list
[/COLOR][/U][/COLOR]```

[COLOR=Sienna]# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock ## Cairo-Dock-Stable
wget -q [http://repository.cairo-dock.org/cairo-dock.gpg](http://repository.cairo-dock.org/cairo-dock.gpg) -O-
 sudo apt-key add -  [/COLOR]
```

---

### Post by Tralce on 2010-03-04
This line needs to go, for one thing: 
```
wget -q http://repository.cairo-dock.org/cairo-dock.gpg -O-
 sudo apt-key add -  
```

Copy this verbatim and paste in the terminal:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Not really sure how that line got added to your /etc/apt/sources.list but that ain't right. 

More info here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by tylerjfisher on 2010-03-04
[COLOR=Sienna][COLOR=Black]It's still not liking my source list. :|
[/COLOR]  
```
E: Type 'clear' is not known on line 54 in source list /etc/apt/sources.list
```[COLOR=Black]Does this just mean I'm supposed to delete "clear" from the source.list?[/COLOR]
```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ karmic universe
deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://repository.cairo-dock.org/ubuntu karmic cairo-dock ## Cairo-Dock-Stable
deb http://repository.cairo-dock.org/ubuntu karmic cairo-dock ## Cairo-Dock-Stable
deb http://repository.cairo-dock.org/ubuntu karmic cairo-dock ## Cairo-Dock-Stable


clear




deb http://ca.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
```[/COLOR]

---

### Post by Thomas Garman on 2010-03-04
I was having problem with the Medibuntu repository a little while ago.  But I just waited for a while and redid the exact same script from:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```


And after a couple of tries it worked

---

### Post by Tralce on 2010-03-04
Somehow the word clear is in there, now. 

The only thing that should be in that file, apart from the comment lines beginning with a # pound sign, are in the following format:
deb [http://address.com/](http://address.com/) ubunturelease description
deb-src [http://address.com/](http://address.com/) ubunturelease description

For example:
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe

Therefore, if a line does not begin with a "#", "deb" or "deb-src" it DOES NOT belong in that file.

---

