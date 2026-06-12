---
title: "UMD Firefox 3.6.2 extensions.rdf/cache/ini not properly regenerated"
date: 2010-01-30
forum: General Help
---

### Post by jdb2 on 2010-01-30
I've been having problems with [Virtus Designs]("http://www.virtusdesigns.net/") [Aero Fox]("http://www.virtusdesigns.net/?page_id=258") theme ever since I received an update from Firefox 3.5.8 to Firefox 3.6 from the [Ubuntu Mozilla Daily]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa") repository. Specifically, the theme seemed to be causing various intolerable graphical glitches. So, after performing a Google search, I found the instructions for removing problematic extensions on [this]("http://kb.mozillazine.org/Firefox_:_FAQs_:_Uninstall_Extensions") page. The instructions indicated that I should delete extensions.rdf , extensions.ini and extensions.cache as well as the subfolder under the extensions folder corresponding to the problematic extension after which restarting Firefox would regenerate the above files. Well, they were regenerated, but Firefox failed to pick up the remaining extensions causing everything to disappear from Tools->Addons->Extensions.

Is there anyway to reverse this or somehow get Firefox to correctly autogenerate the above files?

Any help is appreciated.

Regards,

jdb2

My system info : 

'uname -a' :

Linux jdb2-Kubuntu-temp 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

'lsb_release -a' : 

LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic

'kde4-config --version' : 

Qt: 4.5.2
KDE: 4.3.5 (KDE 4.3.5)
kde4-config: 1.0

'apt-cache policy firefox' :

firefox:
  Installed: 3.6.2~hg20100130r33550+nobinonly-0ubuntu1~umd1~karmic
  Candidate: 3.6.2~hg20100130r33550+nobinonly-0ubuntu1~umd1~karmic
  Version table:
 *** 3.6.2~hg20100130r33550+nobinonly-0ubuntu1~umd1~karmic 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
        100 /var/lib/dpkg/status
     3.5.7+nobinonly-0ubuntu0.9.10.1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
     3.5.3+build1+nobinonly-0ubuntu6 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages

---

