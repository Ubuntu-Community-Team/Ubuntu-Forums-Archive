---
title: "can't install libgtk2.0-dev with package manager"
date: 2006-03-17
forum: General Help
---

### Post by MaaSTaaR on 2006-03-17
Hello ...

when i try install libgtk2.0-dev with GUI package manager it's show for me this massege :

libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.8.6-0ubuntu2.1) but 2.8.6-0ubuntu2 is to be installed
 Depends: libglib2.0-dev (>=2.7.1) but it is not installable
 Depends: libpango1.0-dev (>=1.10.0-2) but it is not installable
 Depends: libatk1.0-dev (>=1.6.1-2) but it is not installable
 Depends: libcairo2-dev  but it is not installable
 Depends: libxinerama-dev  but it is not installable
 Depends: libxrandr-dev  but it is not installable
 Depends: libxcursor-dev  but it is not installable
 Depends: libxfixes-dev  but it is not installable

why it's not installable and what i should do to install these packages ?

---

### Post by Perfect Storm on 2006-03-17
How do your sourcelist looks like? Have you tried with reload before installing the package?

---

### Post by MaaSTaaR on 2006-03-17
hi ...

this is my source.list file :

```

deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##" from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

```

---

### Post by Ignite_nz on 2006-03-17
Try typing ```
 sudo apt-get update
``` This will syncrhonise your package lists with the server's and it should let you install libgtk.

---

### Post by MaaSTaaR on 2006-03-17
hi ...

this is result :

```

Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:5 http://archive.ubuntu.com breezy-updates Release [30.9kB]
Get:6 http://security.ubuntu.com breezy-security Release [27.0kB]
Ign http://packages.freecontrib.org breezy Release.gpg
Get:7 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Ign http://packages.freecontrib.org breezy Release
Ign http://packages.freecontrib.org breezy/free Packages
Ign http://security.ubuntu.com breezy-security Release
Ign http://archive.ubuntu.com breezy-backports Release
Get:8 http://archive.ubuntu.com breezy/main Packages [585kB]
Ign http://packages.freecontrib.org breezy/non-free Packages
Ign http://packages.freecontrib.org breezy/free Sources
Hit http://security.ubuntu.com breezy-security/main Packages
Ign http://packages.freecontrib.org breezy/non-free Sources
Hit http://packages.freecontrib.org breezy/free Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://packages.freecontrib.org breezy/non-free Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Get:9 http://security.ubuntu.com breezy-security/universe Sources [4750B]
Hit http://packages.freecontrib.org breezy/free Sources
Hit http://security.ubuntu.com breezy-security/multiverse Sources
Hit http://packages.freecontrib.org breezy/non-free Sources
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Sources
Get:10 http://archive.ubuntu.com breezy-updates/main Packages [36.0kB]
Get:11 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:12 http://archive.ubuntu.com breezy-updates/main Sources [17.5kB]
Get:13 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:14 http://archive.ubuntu.com breezy-backports/main Packages [14.0kB]
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 717kB in 4m30s (2653B/s)
Reading package lists... Done
W: GPG error: http://security.ubuntu.com breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com breezy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

---

### Post by MaaSTaaR on 2006-03-17
Hello ...

it's work fine now , thanks guys :)

---

