---
title: "And how to get rid of this?"
date: 2006-02-04
forum: General Help
---

### Post by Rasymas on 2006-02-04
Greetings people ;)

Here's what's happening each time i use "Synaptic", and command "sudo apt-get update".

**Synaptic:**
```
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-custom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/madwifi Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_madwifi_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

```

**sudo apt-get update**
```
Ign file: ./ Release.gpg
Ign file: ./ Release
Ign file: ./ Packages
Ign http://deb.opera.com etch Release.gpg
Ign http://deb.opera.com etch Release
Ign http://deb.opera.com etch/non-free Packages
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://deb.opera.com etch/non-free Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release.gpg
Ign http://wine.sourceforge.net binary/ Release.gpg
Hit http://archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy-updates Release
Get:4 http://security.ubuntu.com breezy-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://security.ubuntu.com breezy-security Release
Get:5 ftp://ftp.free.fr breezy Release.gpg
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Ign ftp://ftp.free.fr breezy Release.gpg
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Ign http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Hit http://wine.sourceforge.net binary/ Release
Ign http://public.planetmirror.com breezy Release.gpg
Get:6 ftp://ftp.free.fr breezy Release
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Err http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
  404 Not Found
Ign http://wine.sourceforge.net binary/ Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Hit http://archive.ubuntu.com breezy-backports/main Sources
Hit http://archive.ubuntu.com breezy-backports/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/universe Sources
Hit http://archive.ubuntu.com breezy-backports/multiverse Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Err http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
  404 Not Found
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Err http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
  404 Not Found
Hit http://wine.sourceforge.net binary/ Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Get:7 http://seveas.ubuntulinux.nl breezy-seveas Release.gpg [307B]
Ign http://public.planetmirror.com breezy Release
Hit http://seveas.ubuntulinux.nl breezy-seveas Release
Ign http://seveas.ubuntulinux.nl breezy-seveas Release
Ign http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Packages
Ign http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Packages
Ign http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Packages
Hit http://seveas.ubuntulinux.nl breezy-seveas/freenx Packages
Ign http://seveas.ubuntulinux.nl breezy-seveas/madwifi Packages
Ign http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Sources
Ign http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Sources
Ign http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Sources
Hit http://seveas.ubuntulinux.nl breezy-seveas/freenx Sources
Ign http://seveas.ubuntulinux.nl breezy-seveas/madwifi Sources
Err http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Packages
  404 Not Found
Err http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Packages
  404 Not Found
Err http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Packages
  404 Not Found
Err http://seveas.ubuntulinux.nl breezy-seveas/madwifi Packages
  404 Not Found
Err http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Sources
  404 Not Found
Err http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Sources
  404 Not Found
Err http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Sources
  404 Not Found
Err http://seveas.ubuntulinux.nl breezy-seveas/madwifi Sources
  404 Not Found
Ign ftp://ftp.free.fr breezy Release
Get:8 ftp://ftp.free.fr breezy/free Packages
Ign ftp://ftp.free.fr breezy/free Packages
Get:9 ftp://ftp.free.fr breezy/non-free Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Get:10 ftp://ftp.free.fr breezy/free Sources
Ign http://public.planetmirror.com breezy/free Packages
Ign ftp://ftp.free.fr breezy/free Sources
Get:11 ftp://ftp.free.fr breezy/non-free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Hit ftp://ftp.free.fr breezy/free Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Hit ftp://ftp.free.fr breezy/non-free Sources
Ign http://public.planetmirror.com breezy/non-free Packages
Err http://public.planetmirror.com breezy/free Packages
  302 Found [IP: 203.16.234.91 80]
Err http://public.planetmirror.com breezy/non-free Packages
  302 Found [IP: 203.16.234.91 80]
Fetched 311B in 7s (41B/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://seveas.ubuntulinux.nl/dists/breezy-seveas/breezy-backports/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://seveas.ubuntulinux.nl/dists/breezy-seveas/breezy-custom/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://seveas.ubuntulinux.nl/dists/breezy-seveas/breezy-extras/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://seveas.ubuntulinux.nl/dists/breezy-seveas/madwifi/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://seveas.ubuntulinux.nl/dists/breezy-seveas/breezy-backports/source/Sources.gz  404 Not Found
Failed to fetch http://seveas.ubuntulinux.nl/dists/breezy-seveas/breezy-custom/source/Sources.gz  404 Not Found
Failed to fetch http://seveas.ubuntulinux.nl/dists/breezy-seveas/breezy-extras/source/Sources.gz  404 Not Found
Failed to fetch http://seveas.ubuntulinux.nl/dists/breezy-seveas/madwifi/source/Sources.gz  404 Not Found
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz  302 Found [IP: 203.16.234.91 80]
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz  302 Found [IP: 203.16.234.91 80]
Reading package lists... Done
W: GPG error: http://seveas.ubuntulinux.nl breezy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-custom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/madwifi Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_madwifi_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I think the problem is somewhere in the repositories, so here's the list of them:

[[IMG]http://img485.imageshack.us/img485/604/repositories14je.png[/IMG]](http://imageshack.us)
[[IMG]http://img485.imageshack.us/img485/1897/repositories27ss.png[/IMG]](http://imageshack.us)
[[IMG]http://img485.imageshack.us/img485/7431/repositories30oy.png[/IMG]](http://imageshack.us)
[[IMG]http://img485.imageshack.us/img485/5245/repositories47eh.png[/IMG]](http://imageshack.us)

And here's my ...sources.list :
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb file:///home/arnoldas/gcc-3.4 ./ 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free
deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
## created by arnieplanetremoved

```

Any solutions how to get rid of these errors and warnings? 

Thanks in advance :wink:

---

### Post by astoltz on 2006-02-04
In the Synaptic repositories list, uncheck the "public.planetmirror.com", "seveas.ubuntulinux.nl", and "ubuntu-backports.mirrormax.net" repositories.  Then reload the package list.  

When apt-get says "Couldn't stat source..." it means it couldn't connect to those repositories.

---

