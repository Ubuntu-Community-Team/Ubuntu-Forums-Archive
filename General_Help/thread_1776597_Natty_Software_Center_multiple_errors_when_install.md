---
title: "Natty Software Center multiple errors when installing ~ unlike others"
date: 2011-06-06
forum: General Help
---

### Post by breardon on 2011-06-06
Yesterday evening the Ubuntu Software Center began to display the following errors when I attempt to install anything. 
>  
**Failed to download package files **Check your Internet connection.

My internet works fine so I am completely puzzled with this error; but, when x'ing out of that error 
> 
**Requires installation of untrusted packages** The action would require the installation of packages from not authenticated sources. 

When I x out of this error, it repeats itself for a second time. Upon x'ing again, the errors cease and the installation stops. 
However, I am able to install from terminal fine. 

My initial instinct is to run "**sudo apt-get upgrade"** and everything is up to date. When running "**sudo apt-get update"** and I receive the following errors in terminal after fetching all packages
> 
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release: Unknown error executing gpgv
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release: Unknown error executing gpgv

The most similar case to mine I could find is the error some had regarding the public keys; however, mine is an unknown error.
[http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)

When running gpgv in terminal, I receive the error
> 
gpgv: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC

When attempting to open libreadline.so.6 I receive the error
> 
Could not display "/usr/local/lib/libreadline.so.6". There is no application installed for shared library files. 

At this point, I am unsure if this issue is even related to my error with Ubuntu Software Center. 

I also read others had this issue because their clock was set to a future time and/or date; however, I am not having that issue. 

Here is my source list "**/etc/apt/sources.list**"
> 
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty m
ain restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted #Added by softwar
e-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty restricted main multiverse un
iverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates restricted main multi
verse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security restricted main multive
rse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports restricted main multive
rse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports restricted main mul
tiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiver
se universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-proposed restricted main mult
iverse universe #Added by software-properties
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main


And my software sources from Ubuntu Software Center 
[http://img41.imageshack.us/i/othersoftware.png/](http://img41.imageshack.us/i/othersoftware.png/)
[http://img196.imageshack.us/i/ubuntusoftware.png/](http://img196.imageshack.us/i/ubuntusoftware.png/)
[http://img801.imageshack.us/i/updatesd.png/](http://img801.imageshack.us/i/updatesd.png/)
[http://img607.imageshack.us/i/authentication.png/](http://img607.imageshack.us/i/authentication.png/)

I noticed in my sources list it describes some notes as restricted; however, I am hesitant to edit the log due to my inexperience and unfamiliarity with this area of the operating system. I am fairly new with linux as I began a month ago for research purposes.

This is not a major inconvenience, as I can still download programs from terminal; but, it is quite annoying and certainty is a bug that has been causing havoc. Any help would be appreciated!

-breardon

---

### Post by breardon on 2011-06-07
bump!

---

### Post by breardon on 2011-06-12
a few days later, bump!

---

### Post by glomerulus on 2011-12-03
hello breardon, any luck with this yet?
i'm trying to fix the same, no luck so far

---

### Post by raja.genupula on 2011-12-03
open update manager ->settings ->download from option change your server to best mirror from your location.

 Edit:
this is everything man
[http://ubuntuforums.org/showthread.php?t=1661773](http://ubuntuforums.org/showthread.php?t=1661773)

---

