---
title: "Failing to update a PPA but which one?"
date: 2010-01-05
forum: General Help
---

### Post by DJ_Peng on 2010-01-05
I've been noticing an odd error when I try to run a sudo apt-get update in the last few days. The gist of the error is shown in this output from the end of the update process:
> Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Fetched 8,101B in 3s (2,588B/s)
W: Failed to fetch [http://ppa.launchpad.net//ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net//ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

I have quite a few PPA's that I use, and I notice the extra slash before the second "ppa" right off, but I have no idea which PPA is giving me trouble. I've gone through my entire sources list and tried to verify that the source data is correct but I still get the error. Is there a way to identify specifically which PPA is being troublesome?

My sources.list
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ karmic main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic universe
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-updates multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-backports main universe multiverse restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse #jaunty-backports

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-security main
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ karmic-security multiverse
deb http://ubuntu.media.mit.edu/ubuntu/ karmic-proposed main multiverse universe restricted

#Debian Stable
# deb http://ftp.us.debian.org/debian/ lenny main #Debian Stable
# deb-src http://ftp.us.debian.org/debian/ lenny main #Debian stable


#AWN Testing PPA
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main #AWN Testing Team PPA
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main #AWN Testing Team PPA

#Andrew Starr-Bochicchio (andrewsomething) PPA
deb http://ppa.launchpad.net/andrewsomething/ppa/ubuntu karmic main #Andrew Starr-Bochicchio (andrewsomething) | Rufscript, Consonance
deb-src http://ppa.launchpad.net/andrewsomething/ppa/ubuntu karmic main #Andrew Starr-Bochicchio (andrewsomething) | Rufscript, Consonance

#Arnaud Guignard PPA | Sonata
deb http://ppa.launchpad.net/aguignard/ppa/ubuntu jaunty main #Arnaud Guignard PPA | JAUNTY Sonata
deb-src http://ppa.launchpad.net/aguignard/ppa/ubuntu jaunty main #Arnaud Guignard PPA | JAUNTY Sonata

#Chromium Daily PPA
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main #chromium-browser

#Compiz Packagers PPA
deb http://ppa.launchpad.net/compiz/ppa/ubuntu karmic main #Compiz Packagers PPA
deb-src http://ppa.launchpad.net/compiz/ppa/ubuntu karmic main #Copmpiz Packagers PPA

#directhex PPA | Mono-Moonlight
deb http://ppa.launchpad.net/directhex/ppa/ubuntu karmic main #directhex | Mono-Moonlight
deb-src http://ppa.launchpad.net/directhex/ppa/ubuntu karmic main #directhex | Mono-Moonlight

#Dropbox
deb http://linux.getdropbox.com/ubuntu jaunty main #Dropbox JAUNTY
deb-src http://linux.getdropbox.com/ubuntu jaunty main #Dropbox JAUNTY

#Electric Sheep PPA
# deb http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main #Electric Sheep (Intrepid) disabled on upgrade to karmic
# deb-src http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main #Electirc Sheep (Intrepid) disabled on upgrade to karmic

#Geany Devs PPA
deb http://ppa.launchpad.net/geany-dev/ppa/ubuntu karmic main #Geany Devs
deb-src http://ppa.launchpad.net/geany-dev/ppa/ubuntu karmic main #Geany Devs

#GNOME Do PPA
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main #Do-core PPA
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main #Do-core PPA

#GNOME Do Testers PPA
deb http://ppa.launchpad.net/do-testers/ppa/ubuntu jaunty main #Do Testers PPA JAUNTY
deb-src http://ppa.launchpad.net/do-testers/ppa/ubuntu jaunty main #Do Testers PPA JAUNTY

#Giftwrap PPA
# deb http://ppa.launchpad.net/giftwrap/ppa/ubuntu jaunty main #GiftWrap
# deb-src http://ppa.launchpad.net/giftwrap/ppa/ubuntu jaunty main #GiftWrap

#gGadgets PPA

#Globalmenu PPA
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main #GlobalMenu JAUNTY
deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main #GlobalMenu JAUNTY

#jacobrepo PPA | Zaz

#Jaunty Bleed PPA

#Julien Lavergne Backports PPA (gilir) | Screenlets, Epiphany Webkit
deb http://ppa.launchpad.net/gilir/backports/ubuntu karmic main #Julien Lavergne Backports PPA (gilir) | Screenlets, Epiphany Webkit
deb-src http://ppa.launchpad.net/gilir/backports/ubuntu karmic main #Julien Lavergne Backports PPA (gilir) | Screenlets, Epiphany Webkit

#Michael Vogt (mvo) PPA | Compiz, Clutter
deb http://ppa.launchpad.net/mvo/ppa/ubuntu karmic main #Michael Vogt (mvo) | Compiz, Clutter
deb-src http://ppa.launchpad.net/mvo/ppa/ubuntu karmic main #Michael Vogt (mvo) | Compiz, Clutter

#Moovdia Packagers PPA
deb http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu karmic main #Moovdia
deb-src http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu karmic main #Moovida

#OpenMetaverse PPA
deb http://ppa.launchpad.net/openmetaverse/ppa/ubuntu jaunty main #Open Metaverse Viewer JAUNTY
deb-src http://ppa.launchpad.net/openmetaverse/ppa/ubuntu jaunty main #Open Metaverse Viewer JAUNTY

#OpenOffice Scribblers PPA
# deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main #OpenOffice Scribblers PPA JAUNTY
# deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main #OpenOffice Scribblers PPA JAUNTY

#Philip Newborough (corenomial) PPA | Liberation fonts
deb http://ppa.launchpad.net/corenominal/ppa/ubuntu jaunty main #Philip Newborough | JAUNTY Liberation Fonts
deb-src http://ppa.launchpad.net/corenominal/ppa/ubuntu jaunty main #Philip Newborough | JAUNTY Liberation Fonts

#Rohan Agrawla PPA | Emerald Themes
deb http://ppa.launchpad.net/agrawalr/ppa/ubuntu jaunty main #Rohan Agrawla | Emerald Themes
deb-src http://ppa.launchpad.net/agrawalr/ppa/ubuntu jaunty main #Rohan Agrawal | Emerald Themes

#Saïvann Carignan PPA | GnuCash, Compiz
deb http://ppa.launchpad.net/saivann/ppa/ubuntu jaunty main #Saïvann Carignan | JAUNTY GnuCash, Compiz
deb-src http://ppa.launchpad.net/saivann/ppa/ubuntu jaunty main #Saïvann Carignan | JAUNTY GnuCash, Compiz

#Seed PPA
deb http://ppa.launchpad.net/orange-owners/ppa/ubuntu karmic main #Seed PPA
deb-src http://ppa.launchpad.net/orange-owners/ppa/ubuntu karmic main #Seed PPA

#Telepathy Team PPA

#Test for new Nautilus UI PPA

#TualatriX PPA | UTweak
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main #TualatriX | UTweak
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main #TualatriX | UTweak

#Ubuntu One Beta Testers PPA
# deb http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main #Ubuntu One Beta Testers PPA
# deb-src http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main #Ubuntu One Beta Testers PPA

#Ubuversal Applets (nee Screenlets)
deb http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_9.04/ ./ #Universal Applets (nee Screenlets) JAUNTY

#Vala Team PPA
deb http://ppa.launchpad.net/vala-team/ppa/ubuntu karmic main #Vala Team PPA
deb-src http://ppa.launchpad.net/vala-team/ppa/ubuntu karmic main #Vala Team PPA

#Webkit Team PPA
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu karmic main #Webkit Team PPA
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu karmic main #WebKit Team PPA

#Webkit Team - Epiphany PPA
deb http://ppa.launchpad.net/webkit-team/epiphany/ubuntu karmic main #WebKit Team - Epiphany PPA
deb-src http://ppa.launchpad.net/webkit-team/epiphany/ubuntu karmic main #WebKit Team - Epiphany PPA

#Wine Team PPA
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main #Wine Team PPA
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main #Wine Team PPA


#Cairo dock
# deb http://repository.cairo-dock.org/ubuntu karmic cairo-dock #Cairo-dock

#Google Linux Repos
deb http://dl.google.com/linux/deb/ stable non-free #Google Stable
deb http://dl.google.com/linux/deb/ testing non-free #Google Testing

#Griffith
deb ftp://ftp.berlios.de/pub/griffith/ ./ #Griffith

#Opera (borked?)
deb http://deb.opera.com/opera/ lenny non-free #opera

#wicd
# deb http://apt.wicd.net hardy extras #Wicd disabled on upgrade to karmic
# deb http://ftp.de.debian.org/debian squeeze main #Debian Squeeze (testing)

# deb http://packages.medibuntu.org/ karmic-staging free non-free #Medibuntu karmic-staging non-free
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse #Sun Java5
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse #Sun Java5 updates

```

The complete output from the update
```
:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Hit http://ubuntu.media.mit.edu karmic Release.gpg
Ign http://ubuntu.media.mit.edu karmic/main Translation-en_US
Ign http://ubuntu.media.mit.edu karmic/restricted Translation-en_US
Ign http://ubuntu.media.mit.edu karmic/universe Translation-en_US
Ign http://ubuntu.media.mit.edu karmic/multiverse Translation-en_US
Hit http://ubuntu.media.mit.edu karmic-updates Release.gpg
Ign http://ubuntu.media.mit.edu karmic-updates/main Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-updates/restricted Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-updates/universe Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-updates/multiverse Translation-en_US
Hit http://ubuntu.media.mit.edu karmic-backports Release.gpg
Ign http://ubuntu.media.mit.edu karmic-backports/main Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-backports/universe Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-backports/multiverse Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-backports/restricted Translation-en_US
Hit http://ubuntu.media.mit.edu karmic-security Release.gpg
Ign http://ubuntu.media.mit.edu karmic-security/main Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-security/restricted Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-security/universe Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-security/multiverse Translation-en_US
Hit http://ubuntu.media.mit.edu karmic-proposed Release.gpg
Ign http://ubuntu.media.mit.edu karmic-proposed/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com stable/non-free Translation-en_US
Ign http://dl.google.com stable/main Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-proposed/multiverse Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-proposed/universe Translation-en_US
Ign http://ubuntu.media.mit.edu karmic-proposed/restricted Translation-en_US
Hit http://ubuntu.media.mit.edu karmic Release
Hit http://ubuntu.media.mit.edu karmic-updates Release
Hit http://ubuntu.media.mit.edu karmic-backports Release
Hit http://ubuntu.media.mit.edu karmic-security Release
Hit http://ubuntu.media.mit.edu karmic-proposed Release
Ign http://linux.getdropbox.com jaunty Release.gpg
Ign http://linux.getdropbox.com jaunty/main Translation-en_US
Get:2 http://dl.google.com testing Release.gpg [189B]
Ign http://dl.google.com testing/non-free Translation-en_US
Get:3 http://dl.google.com stable Release [2,540B]
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US
Hit http://packages.medibuntu.org karmic Release.gpg
Ign http://packages.medibuntu.org karmic/free Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://linux.getdropbox.com jaunty Release
Hit http://archive.getdeb.net karmic-getdeb Release.gpg
Ign http://archive.getdeb.net karmic-getdeb/apps Translation-en_US
Hit http://ubuntu.media.mit.edu karmic/main Packages
Hit http://deb.opera.com lenny Release.gpg
Ign http://deb.opera.com lenny/non-free Translation-en_US
Hit http://archive.canonical.com karmic Release
Hit http://ubuntu.media.mit.edu karmic/restricted Packages
Hit http://ubuntu.media.mit.edu karmic/main Sources
Hit http://ubuntu.media.mit.edu karmic/universe Packages
Hit http://ubuntu.media.mit.edu karmic/universe Sources
Hit http://ubuntu.media.mit.edu karmic/multiverse Packages
Hit http://ubuntu.media.mit.edu karmic/multiverse Sources
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Hit http://packages.medibuntu.org karmic Release
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Ign http://linux.getdropbox.com jaunty/main Packages
Get:4 http://dl.google.com testing Release [2,513B]
Ign http://download.opensuse.org ./ Release.gpg
Hit http://ubuntu.media.mit.edu karmic-updates/main Packages
Hit http://ubuntu.media.mit.edu karmic-updates/restricted Packages
Hit http://ubuntu.media.mit.edu karmic-updates/main Sources
Hit http://ubuntu.media.mit.edu karmic-updates/universe Packages
Hit http://ubuntu.media.mit.edu karmic-updates/universe Sources
Hit http://ubuntu.media.mit.edu karmic-updates/multiverse Packages
Hit http://ubuntu.media.mit.edu karmic-updates/multiverse Sources
Hit http://ubuntu.media.mit.edu karmic-backports/main Packages
Hit http://ubuntu.media.mit.edu karmic-backports/universe Packages
Hit http://ubuntu.media.mit.edu karmic-backports/multiverse Packages
Hit http://ubuntu.media.mit.edu karmic-backports/restricted Packages
Ign http://linux.getdropbox.com jaunty/main Sources
Hit http://archive.getdeb.net karmic-getdeb Release
Hit http://ubuntu.media.mit.edu karmic-security/main Packages
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Hit http://deb.opera.com lenny Release
Hit http://ubuntu.media.mit.edu karmic-security/restricted Packages
Hit http://ubuntu.media.mit.edu karmic-security/main Sources
Hit http://ubuntu.media.mit.edu karmic-security/universe Packages
Hit http://ubuntu.media.mit.edu karmic-security/universe Sources
Hit http://ubuntu.media.mit.edu karmic-security/multiverse Packages
Hit http://ubuntu.media.mit.edu karmic-security/multiverse Sources
Hit http://ubuntu.media.mit.edu karmic-proposed/main Packages
Hit http://ubuntu.media.mit.edu karmic-proposed/multiverse Packages
Hit http://ubuntu.media.mit.edu karmic-proposed/universe Packages
Ign http://linux.getdropbox.com jaunty/main Packages
Hit http://ubuntu.media.mit.edu karmic-proposed/restricted Packages
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Ign http://download.opensuse.org ./ Translation-en_US
Ign http://linux.getdropbox.com jaunty/main Sources
Get:5 http://dl.google.com stable/non-free Packages [1,010B]
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://archive.canonical.com karmic/partner Packages
Hit http://ppa.launchpad.net jaunty Release.gpg
Hit http://linux.getdropbox.com jaunty/main Packages
Get:6 http://dl.google.com stable/main Packages [867B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://linux.getdropbox.com jaunty/main Sources
Hit http://packages.medibuntu.org karmic/free Packages
Get:7 http://dl.google.com testing/non-free Packages [793B]
Hit http://archive.canonical.com karmic/partner Sources
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Hit http://packages.medibuntu.org karmic/non-free Packages
Hit http://packages.medibuntu.org karmic/free Sources
Hit http://packages.medibuntu.org karmic/non-free Sources
Hit http://archive.getdeb.net karmic-getdeb/apps Packages
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Ign http://download.opensuse.org ./ Release
Ign http://deb.opera.com lenny/non-free Packages
Ign http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://deb.opera.com lenny/non-free Packages
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Ign http://download.opensuse.org ./ Packages
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Hit http://deb.opera.com lenny/non-free Packages
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Ign http://download.opensuse.org ./ Packages
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release
Hit ftp://ftp.berlios.de ./ Release.gpg
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net jaunty Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net jaunty Release
Hit http://ppa.launchpad.net jaunty Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net jaunty Release
Hit http://ppa.launchpad.net jaunty Release
Hit http://ppa.launchpad.net jaunty Release
Get:8 ftp://ftp.berlios.de ./ Translation-en_US
Hit http://ppa.launchpad.net jaunty Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://download.opensuse.org ./ Packages
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Ign http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Ign ftp://ftp.berlios.de ./ Translation-en_US
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit ftp://ftp.berlios.de ./ Release
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit ftp://ftp.berlios.de ./ Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Ign http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Sources
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net karmic/main Packages
Ign http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Sources
Ign http://ppa.launchpad.net karmic/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Err http://ppa.launchpad.net karmic/main Packages
  404  Not Found
Fetched 8,101B in 3s (2,311B/s)W: Failed to fetch http://ppa.launchpad.net//ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
:~$ 
```

---

### Post by michy99 on 2010-01-05
Edit /etc/apt/sources.list and comment out all the ppa's. Do a sudo apt-get update and you should not get any errors. Now uncomment the ppa's one at a time, doing the update after each change. When you get the error, the problem is the last one you changed.

---

### Post by DJ_Peng on 2010-01-05
I was afraid that was going to be the best solution. With the number of PPA's I use that method is a pain in the rear. I was hoping there was a way to get a verbose output with the sources being checked as it runs.

---

