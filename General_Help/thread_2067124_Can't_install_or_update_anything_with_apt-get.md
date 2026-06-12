---
title: "Can't install or update anything with apt-get"
date: 2012-10-06
forum: General Help
---

### Post by adfrydland on 2012-10-06
Hi there, I've had a look and I can't see that this problem has been posted before. I am running Ubuntu server 12.04 and suddenly I can't seem to install anything using apt-get, when I try an apt-get update as suggested I get the following:```
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources/DiffIndex
Ign [http://www.greyhole.net](http://www.greyhole.net) stable InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources/DiffIndex
Err [http://www.greyhole.net](http://www.greyhole.net) stable Release.gpg
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages/DiffIndex
Ign [http://www.greyhole.net](http://www.greyhole.net) stable Release
Ign [http://www.greyhole.net](http://www.greyhole.net) stable/main amd64 Packages/DiffIndex
Ign [http://www.greyhole.net](http://www.greyhole.net) stable/main i386 Packages/DiffIndex
Ign [http://www.greyhole.net](http://www.greyhole.net) stable/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Err [http://www.greyhole.net](http://www.greyhole.net) stable/main amd64 Packages
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Err [http://www.greyhole.net](http://www.greyhole.net) stable/main i386 Packages
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages/DiffIndex
Err [http://www.greyhole.net](http://www.greyhole.net) stable/main Translation-en_GB
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Err [http://www.greyhole.net](http://www.greyhole.net) stable/main Translation-en
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
```
 
my sources.list is:
```
# 
# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted
#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) precise main
#==================================
# Paissad Repository (pms-linux)  =
#==================================
#deb [http://deb.paissad.net/](http://deb.paissad.net/) unstable main contrib non-free
#deb-src [http://deb.paissad.net/](http://deb.paissad.net/) unstable main contrib
#=============
# mediainfo  =
#=============
#deb [http://ppa.launchpad.net/shiki/mediainfo/ubuntu](http://ppa.launchpad.net/shiki/mediainfo/ubuntu) precise main
#deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) precise main
```
 
Any help you can give would be fantasitc, I'm doing my nut here trying to work out what this could be.
 
Thanks
 
Adam

---

### Post by cway00 on 2012-10-06
> **adfrydland said:**
> Hi there, I've had a look and I can't see that this problem has been posted before. I am running Ubuntu server 12.04 and suddenly I can't seem to install anything using apt-get, when I try an apt-get update as suggested I get the following:```
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources/DiffIndex
Ign [http://www.greyhole.net](http://www.greyhole.net) stable InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources/DiffIndex
Err [http://www.greyhole.net](http://www.greyhole.net) stable Release.gpg
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages/DiffIndex
Ign [http://www.greyhole.net](http://www.greyhole.net) stable Release
Ign [http://www.greyhole.net](http://www.greyhole.net) stable/main amd64 Packages/DiffIndex
Ign [http://www.greyhole.net](http://www.greyhole.net) stable/main i386 Packages/DiffIndex
Ign [http://www.greyhole.net](http://www.greyhole.net) stable/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Err [http://www.greyhole.net](http://www.greyhole.net) stable/main amd64 Packages
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Err [http://www.greyhole.net](http://www.greyhole.net) stable/main i386 Packages
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages/DiffIndex
Err [http://www.greyhole.net](http://www.greyhole.net) stable/main Translation-en_GB
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Err [http://www.greyhole.net](http://www.greyhole.net) stable/main Translation-en
  Something wicked happened resolving 'www.greyhole.net:http' (-11 - System error)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse amd64 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_GB
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en_GB
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
```my sources.list is:
```
# 
# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted
#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/main/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)]/ precise main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) precise main
#==================================
# Paissad Repository (pms-linux)  =
#==================================
#deb [http://deb.paissad.net/](http://deb.paissad.net/) unstable main contrib non-free
#deb-src [http://deb.paissad.net/](http://deb.paissad.net/) unstable main contrib
#=============
# mediainfo  =
#=============
#deb [http://ppa.launchpad.net/shiki/mediainfo/ubuntu](http://ppa.launchpad.net/shiki/mediainfo/ubuntu) precise main
#deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) precise main
```Any help you can give would be fantasitc, I'm doing my nut here trying to work out what this could be.
 
Thanks
 
Adam

What is your source of internet connection?
make sure you could browse from your network connection 
Connect via LAN cable instead wireless.
Switch to main server in software-sources.
[https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)
 If enabled turn off proxies or a blocking ufw.
 
Hope it helps

---

### Post by adfrydland on 2012-10-06
The machine is a server running Ubuntu server so no gui functions. My internet connection is wired, I can ping outside ip's fine and access a webpage hosted on the server from outside my local network. I'm not sure how to switch to main server in software-sources using the command line, I have already tried the following alternative sources.list but to no avail:
```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################
###### Ubuntu Main Repos
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
###### Ubuntu Update Repos
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################
###### 3rd Party Binary Repos
#### SABnzbd - [http://sabnzbd.org/](http://sabnzbd.org/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4BB9F05F
deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) precise main
#### Webmin - [http://www.webmin.com](http://www.webmin.com)
## Run this command: wget [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc) -O- | sudo apt-key add -
deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib
```
 
Not sure I want to turn off proxies untill I'm sure what the current settings are. No firewall settings have changed since it was last working either. 
 
This is what happens when I try and install some new software```
sudo apt-get install procmail
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  procmail
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 155 kB of archives.
After this operation, 381 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  procmail
Install these packages without verification [y/N]? y
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main procmail amd64 3.22-19
  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procmail/procmail_3.22-19_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procmail/procmail_3.22-19_amd64.deb)  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-11 - System error)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
Thanks for the input but still no joy.

---

### Post by plucky on 2012-10-06
> [http://www.greyhole.net](http://www.greyhole.net) stable/main

What is that?

When I click on the link,it just take me to the [webpage](http://www.greyhole.net/).

Could it be a file in **/etc/apt/sources.list.d/**? as it is not showing in your sources.list.

---

### Post by adfrydland on 2012-10-06
> **plucky said:**
> What is that?
 
When I click on the link,it just take me to the [webpage]("http://www.greyhole.net/").
 
Could it be a file in **/etc/apt/sources.list.d/**? as it is not showing in your sources.list.
 
Yes, I have a file greyhole.list containing ```
deb [http://www.greyhole.net/releases/deb](http://www.greyhole.net/releases/deb) stable main
```
I was thinking about using greyhole to manage an array of discs but chickened out, just going to raid it now.

---

