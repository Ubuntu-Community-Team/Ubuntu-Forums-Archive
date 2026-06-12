---
title: "Problems with sources list??"
date: 2006-03-18
forum: General Help
---

### Post by MJSOnline on 2006-03-18
Hi all.  I have a error message when I do I apt-get update command.

The error is...

[B]Err [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release.gpg
  Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26), connection timed out
Fetched 6B in 2m0s (0B/s)
Failed to fetch [http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg](http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg)  Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/breezy-backports Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/breezy-custom Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-custom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/breezy-extras Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/freenx Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_freenx_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/madwifi Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_madwifi_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
matthew@server:~$[/B]

Here is a copy of my Sources List..

[B]deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## Main
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted



## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Archive
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe

## Official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse


## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse


## EXTRAS

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## Opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Seveas
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi


## PLF - [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

## http 100mbit/s mirror provided thanks to OVH ([http://ovh.com](http://ovh.com))
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/B]

I have looked at this list 3 times and can't see the fault.  Can anyone shed any light on this for me?  Thanks.  Matthew

---

### Post by GeneralZod on 2006-03-18
This site appears to be down at the moment:

[http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/)

Not much you can do but wait until it comes back up, I'm afraid :/ It shouldn't affect your ability to install updates from any of  your other sources, though :)

---

### Post by Ignite_nz on 2006-03-18
If you can't be botherd waiting, in your sources list, change all the country codes from 'gb' to something like 'us' for the USA server, or in my case, 'nz' for the New Zealand server.```
deb http://**gb**.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://**gb**.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## Main
deb http://**gb**.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://**gb**.archive.ubuntu.com/ubuntu breezy-updates main restricted



## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://**gb**.archive.ubuntu.com/ubuntu breezy universe
deb-src http://**gb**.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Archive
deb http://**gb**.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://**gb**.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe

## Official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse


## deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse


## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse


## EXTRAS

## Wine
deb http://wine.sourceforge.net/apt/ binary/

## Opera
deb http://deb.opera.com/opera/ etch non-free

## Seveas
deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi


## PLF - http://wiki.ubuntu-fr.org/doc/plf
deb ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ breezy free non-free

## http 100mbit/s mirror provided thanks to OVH (http://ovh.com)
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
```

---

### Post by powder on 2006-03-18
Seveas mirrors. :)

#  deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) breezy-seveas {All Sections}

# deb [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) breezy-seveas {All Sections}

# deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) breezy-seveas {All Sections}

# deb [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) breezy-seveas {All Sections}

# deb [http://users.lichtsnel.nl/~seveas/](http://users.lichtsnel.nl/~seveas/) breezy-seveas {All Sections}

---

### Post by Ignite_nz on 2006-03-18
[QUOTE=powder]Seveas mirrors. :)

#  deb [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) breezy-seveas {All Sections}

# deb [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) breezy-seveas {All Sections}

# deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) breezy-seveas {All Sections}

# deb [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) breezy-seveas {All Sections}

# deb [http://users.lichtsnel.nl/~seveas/](http://users.lichtsnel.nl/~seveas/) breezy-seveas {All Sections}[/QUOTE]Thanks Powder, wasn't too sure on those ones ;)

---

### Post by MJSOnline on 2006-03-19
Cheers guys.  Thanks for the extra mirror sites.  Is there any more sites I can add to the list to make the fullest ultimute sources list?  Thanks again. Matthew

---

### Post by mcduck on 2006-03-19
[QUOTE=MJSOnline]Cheers guys.  Thanks for the extra mirror sites.  Is there any more sites I can add to the list to make the fullest ultimute sources list?  Thanks again. Matthew[/QUOTE]
There's some more here: [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by MJSOnline on 2006-03-19
Thanks mcduck. Nice little site that. Anyone got any more? M

---

### Post by MJSOnline on 2006-03-20
Hi all.  Where is the best place to find mirrors/servers that have packages and sources on them to add to my list?  Thanks.  Matthew

---

