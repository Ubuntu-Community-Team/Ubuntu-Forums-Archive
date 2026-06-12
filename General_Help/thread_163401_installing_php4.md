---
title: "installing php4"
date: 2006-04-20
forum: General Help
---

### Post by rocarm on 2006-04-20
i've tried: 
```

sudo apt-get install php4

```

but it comes up with

```

mark@phone:~$ sudo apt-get install php4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4

```


and my repository list. 
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://au.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://au.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://au.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

can anyone help? I don't want php5, my live server is php4, and the code doens't work in php5. this is supposed to be a dev server. will i have to build php4 from the binaries or is it available via aptget?

---

### Post by Justin.Little on 2006-04-20
[QUOTE=rocarm]

and my repository list. 
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://au.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://au.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://au.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

can anyone help? I don't want php5, my live server is php4, and the code doens't work in php5. this is supposed to be a dev server. will i have to build php4 from the binaries or is it available via aptget?[/QUOTE]

Hey try uncommenting your universe and backports repo's you still have the #'s in front of them. I hope this helps.

---

### Post by rocarm on 2006-04-20
thanks mate, works a charm!

---

