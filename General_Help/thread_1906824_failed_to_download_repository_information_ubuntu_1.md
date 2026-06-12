---
title: "failed to download repository information ubuntu 11.10"
date: 2012-01-10
forum: General Help
---

### Post by sitarammeena on 2012-01-10
Hi everyone 
I am using Ubuntu 11.10 64 bit Intel build machine.
earlier it was updating regularly and now its says " failed to download repository information.. check your internet connection.

my internet connection is working fine as i am browsing and surfing everything on the same computer.

Thanks

---

### Post by plucky on 2012-01-10
> **sitarammeena said:**
> Hi everyone 
I am using Ubuntu 11.10 64 bit Intel build machine.
earlier it was updating regularly and now its says " failed to download repository information.. check your internet connection.

my internet connection is working fine as i am browsing and surfing everything on the same computer.

Thanks

Welcome to the Forum.

Open a terminal and post output of ```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by sitarammeena on 2012-01-11
Hi Plucky 

Thanks for reply ..


_**this is the output of sudo apt-get update**_


W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg](http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg](http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-amd64/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-amd64/Packages)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-amd64/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-amd64/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en](http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/binary-amd64/Packages](http://dl.google.com/linux/earth/deb/dists/stable/main/binary-amd64/Packages)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/earth/deb/dists/stable/main/binary-i386/Packages)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en](http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-proposed/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-amd64/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.



_**and this is the output of cat /etc/apt/sources.list**_

ajay@ajay-CELSIUS-W410:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security universe main multiverse restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-updates universe main multiverse restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-backports universe main multiverse restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric-proposed universe main multiverse restricted

thanks

---

### Post by raja.genupula on 2012-01-11
change your server to other mirror

open update manager -> settings -> at 1st tab , download from option and try again 

all the best.

---

### Post by sitarammeena on 2012-01-11
Hi raja 
thanks dear for your reply..
I have tried with, Mian server, two ther server from INDIA, and many others as well, no one is working.

---

### Post by spacecheck on 2012-01-11
Since you have upgraded to Oneiric, I would suggest you close any package managers and then use the editor to remove any lines related to Natty (for example:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse  ) or at least comment them out by putting a # in front of them (I would also suggest commenting out partner sources, at least until regular updates are working).

Then save the file and try another update with: sudo  apt-get update

If it works, be sure to use the thread tools to mark the thread solved. If the problem remains, try the solution listed here:

[http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3](http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3)

If that doesn't work, report back for further assistance.

Good luck!

---

### Post by raja.genupula on 2012-01-11
Hi do this once

sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

---

### Post by gsgleason on 2012-01-11
The issue appears to be with name resolution.

cat /etc/resolv.conf

'nslookup archive.canonical.com' or 'dig archive.canonical.com'

---

### Post by bluexrider on 2012-01-11
I verified a few of the links and they are working, so It is likely you need to select a different server, possibly outside your country to connect.

---

### Post by sitarammeena on 2012-01-13
Thanks all for reply ..
here is the result of everyone suggested ..

**1.** [B]spacecheck
    [/B]I tried # before all addresses, leaving only one functional at a time in source.list     ...... no one is working.
    I Tried the solution given at  [http://ubuntuforums.org/showthread.p...invalid&page=3]("http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3")      not working.
**2. raja.genupula**

  sudo rm -rf /var/lib/apt/lists/*
  sudo apt-get update  ...... not working

[B]3.bluexrider
 [/B]I tried Main server of ubuntu, Two server from India, from U.S. from Spain and  from   England as well, ....... no one is working  

**4. gsgleason** 	 		 		cat /etc/resolv.conf ... this file is empty just written this line 
" # Generated by NetworkManager"
   OR either i didn't understand what you want to say.

Please Help !!!!!!

Thanking you.

---

### Post by varunendra on 2012-01-13
> **sitarammeena said:**
> 
**4. gsgleason**                       cat /etc/resolv.conf ... [B]this file is [COLOR=Red]empty[/COLOR] just written this line 
" # Generated by NetworkManager"[/B]
   
You understood him correctly to run the command, just run the next command as well -
```
nslookup archive.canonical.com
```
It may give us an idea of current DNS in use (if you really are able to browse internet).

The /etc/resolv.conf file should have contained the IP address of your current DNS server(s), but it does not. In that case, you should not be able to browse internet, but you say you are. I'm not sure, but it seems that perhaps you are using pppoe or wvdial or something similar to get connected to internet, while the updater is looking in its favourite /etc/resolv.conf file for nameservers, where it obviously gets nothing!

**_Short solution_: **Open Network Manager, goto 'edit' connection you are using, and add your DNS in the DNS field if you know it, or **4.2.2.2, 4.2.2.4** (google's open dns) if you don't know it.

If having problems, please post the output of:
```
ifconfig -a
cat /etc/network/interfaces
nslookup archive.canonical.com
```

---

### Post by eumonmaz on 2012-01-13
[SIZE=3]I have the same problem as you, I think.
I've installed ubuntu 11.10 desktop.
I'm trying to add putty and other package using UCK to make a personalized livecd.
When I try to install UCK from ubuntu center, it fails saing:
 "Fail to download informations from repository "
 "check internet connection"
:A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release: The following signatures were invalid: NODATA 2
, W:A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: NODATA 2
, E:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: NODATA 2

The internet connection is find (there is a firewall at my workplace).
Trying by command line

[/SIZE][SIZE=3][COLOR=Blue]eugenio@CLTI-30:~$ sudo apt-get install uck[/COLOR][/SIZE][SIZE=3]
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
O pacote uck não está disponível, mas é referenciado por outro pacote.
Isto pode significar que o pacote está faltando, ficou obsoleto ou
está disponível somente a partir de outra fonte

E: O pacote 'uck' não tem candidato para instalação
[/SIZE][SIZE=3][COLOR=Blue]eugenio@CLTI-30:~$ sudo apt-get update[/COLOR][/SIZE][SIZE=3]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease

eugenio@CLTI-30:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease              
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg               
Atingido [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease      
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                   
Atingido [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease    
Obter:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]                  
Atingido [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                         
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources              
Obter:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]          
Obter:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [593 B]            
Obter:4 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [14 B]  
Obter:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg [198 B]        
Obter:6 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [8.189 B] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Obter:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release [40,8 kB]                    
Obter:8 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [653 B] 
Atingido [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [593 B]           
Obter:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release [40,8 kB]                    
**[COLOR=Red]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release    [/COLOR]**                              
  
Obter:10 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [65,2 kB]
Obter:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release [40,8 kB]           
**[COLOR=Red]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release [/COLOR]**                         
  
Obter:12 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Obter:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release [40,8 kB]         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release                        
W: Um erro ocorreu durante a verificação da assinatura. O repositório não foi atualizado eo índice anterior de arquivo será usado. Erro GPG: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release:As seguintes assinaturas eram inválidas: NODATA 2

W: Um erro ocorreu durante a verificação da assinatura. O repositório não foi atualizado eo índice anterior de arquivo será usado. Erro GPG: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release:As seguintes assinaturas eram inválidas: NODATA 2

E: Erro GPG: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release: As seguintes assinaturas eram inválidas: NODATA 2


 
[/SIZE][SIZE=3][COLOR=Blue]eugenio@CLTI-30:~$ cat /etc/apt/sources.list[/COLOR][/SIZE][SIZE=3]
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

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

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

Any sugestion?,
thanks in advance


[/SIZE]

---

### Post by spacecheck on 2012-01-13
> **eumonmaz said:**
> [SIZE=3]

Any sugestion?,
thanks in advance
[/SIZE]
Yes, please start a new thread for your problem, which does appear to be different from that of the OP.

Thanks!

---

### Post by spacecheck on 2012-01-13
> **sitarammeena said:**
> Hi Plucky 

Thanks for reply ..


_**...**_
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
...
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
...

thanks

Make sure all of the package managers are closed and then completely remove the above lines related to natty and also put a comment before the lines related to "partner" (at least for now). Then try again.

---

### Post by sitarammeena on 2012-01-17
Thank everyone reply.

**_I. Result of varunendra__'s solution_******

yeah I am using Internet connection without any problem of not adding DNS earlier.
now I am added the DNS as well and the out put of of the command 
   1. cat /etc/resolv.conf
   # Generated by NetworkManager
     nameserver 202.41.10.31

still no solution.

_**2. out put of the ifconfig -a**_
     ajay@ajay-CELSIUS-W410:~$ ifconfig -a
     eth0      Link encap:Ethernet  HWaddr 00:19:99:a7:e0:a2  
          inet addr:172.16.8.135  Bcast:172.16.9.255  Mask:255.255.254.0
          inet6 addr: fe80::219:99ff:fea7:e0a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51490 errors:0 dropped:40 overruns:0 frame:0
          TX packets:21704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23266353 (23.2 MB)  TX bytes:4660702 (4.6 MB)
          Interrupt:20 Memory:fb100000-fb120000 

  lo        Link encap:Local Loopback  
             inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:17765 errors:0 dropped:0 overruns:0 frame:0
           TX packets:17765 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
           RX bytes:891074 (891.0 KB)  TX bytes:891074 (891.0 KB)

   **_3. output of the cat /etc/network/interfaces_** 

   ajay@ajay-CELSIUS-W410:~$ cat /etc/network/interfaces 
   auto lo
   iface lo inet loopback

    **_4. output of the command nslookup archive.canonical.com_**
  
  ajay@ajay-CELSIUS-W410:~$ nslookup archive.canonical.com
  ;; connection timed out; no servers could be reached

**no solution still....**
[B]
II. spacecheck[/B]
I did your solution ... but not works...


Thanking you all for reply...

Please help it not working yet.

---

### Post by varunendra on 2012-01-17
> **sitarammeena said:**
> 
   1. cat /etc/resolv.conf
   # Generated by NetworkManager
     nameserver 202.41.10.31
Have you tried [s]google's[/s] open ones (**4.2.2.2, 4.2.2.4**) [COLOR=Red]*(EDIT: these are not google's DNS servers)*[/COLOR]  also? The above one you mentioned seems to be related with JNU's private network and as such, may be restricted or limited in certain ways.

Can you manually browse [http://archive.canonical.com/](http://archive.canonical.com/) ?

---

### Post by sitarammeena on 2012-01-17
Thank you very much every one whomever replied fro my problem.

Now the problem is solved.

 it was a DNS problem. In the initial, there is no DNS was added my  Internet was working fine but the problem was with the update. Than I  added my Institutes's own  DNS, it was also not works and than last as  suggested by the Varun I added _**"google's open ones (4.2.2.2)" **_in the Internet settings.

How to do it....

1. go to the Network Connections.
2. select your connections whichever you are using.
3. do edit
4. in this popup use the tab which type connection you are using like.. IPv4, TPv6...
5. add the DNS Server _**4.2.2.2**_ and save it.
6. close all window and restart your computer and that's it.


Thank you all.

---

### Post by BlinkinCat on 2012-01-17
You could mark this thread as "solved" using thread tools at top of page - :)

---

### Post by varunendra on 2012-01-17
Hi sitarammeena,

Glad to hear it worked. However, for optimal performance you might want to try a few others as well: [http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/)

(By the way, as the above linked site says, it seems I was wrong in assuming that 4.2.2.2 or 4.2.2.4 are Google's. They are not).

Also, consider adding a secondary one as well (separated by a comma in the NetworkManager's DNS field - i.e., point#5 in your last post).

Most people suggest google's (yes this time I'm definitely correct ;)) 8.8.8.8 and 8.8.4.4. But I am doubtful about their consistency as yesterday pinging both of them resulted in packet losses for me (although today they are replying just fine). So I'd say try many of the available ones and choose the ones that seem best for you.



**_PS_:**
Please mark the thread as **[Solved]** as *BlinkinCat *suggested above (or follow my signature to _*See How*_ to do it)

---

