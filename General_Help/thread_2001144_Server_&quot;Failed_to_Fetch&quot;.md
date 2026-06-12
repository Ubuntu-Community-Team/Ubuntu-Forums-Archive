---
title: "Server &quot;Failed to Fetch&quot;"
date: 2012-06-10
forum: General Help
---

### Post by Beastt on 2012-06-10
Hey, I'm happily running Ubuntuserver 11.10 64-bit and 2 days ago, i wanted to reinstall apache2 so I did that and php and mysql and after that it seems when I try to reinstall it it says the without verification thing and put "y" and it gives me errors. And it gives me similar errors when i run apt-get update....


> 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://www.plexapp.com/repo/dists/lucid/main/i18n/Translation-en_US](http://www.plexapp.com/repo/dists/lucid/main/i18n/Translation-en_US)  Something wicked happened resolving 'www.plexapp.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://www.plexapp.com/repo/dists/lucid/main/i18n/Translation-en](http://www.plexapp.com/repo/dists/lucid/main/i18n/Translation-en)  Something wicked happened resolving 'www.plexapp.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_US)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.



Sources.list:

> 
# 

# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release i386 (20111011)]/ oneiric main restricted

#deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release i386 (20111011)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb [http://www.plexapp.com/repo](http://www.plexapp.com/repo) lucid main
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main


---

### Post by Beastt on 2012-06-10
Fixed, it was a dns thing... not sure why.

---

