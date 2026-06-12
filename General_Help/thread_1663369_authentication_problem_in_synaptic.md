---
title: "authentication problem in synaptic"
date: 2011-01-09
forum: General Help
---

### Post by r.stiltskin on 2011-01-09
I want to install CodeBlocks 10.05 using the Codeblocks Debian binary package from [http://www.codeblocks.org/downloads/26#linux]("http://www.codeblocks.org/downloads/26#linux"), which requires upgrading to a newer version of wxwidgets than Ubuntu provides.  So I followed the instructions at [wxpython.org]("http://wiki.wxpython.org/InstallingOnUbuntuOrDebian") adding their gpg key and adding their repositories to my sources.list.  But when I ask Synaptic to Mark All Upgrades, it warns:
> You are about to install software that **can't be authenticated!** etc., etc...


In Settings/Repositories/Authentication Robin Dunn's (the xwPython creator) key is listed, and if I simply run
sudo apt-get -s upgrade
in a terminal, apt doesn't complain at all.  It gives:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libwxbase2.8-0 libwxbase2.8-dev libwxgtk2.8-0 libwxgtk2.8-dev wx-common
  wx2.8-doc wx2.8-examples wx2.8-headers
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst libwxgtk2.8-dev [2.8.10.1-0ubuntu1.2] (2.8.11.0-0 apt.wxwidgets.org) []
Inst libwxbase2.8-dev [2.8.10.1-0ubuntu1.2] (2.8.11.0-0 apt.wxwidgets.org) []
Inst wx2.8-headers [2.8.10.1-0ubuntu1.2] (2.8.11.0-0 apt.wxwidgets.org) []
Inst libwxgtk2.8-0 [2.8.10.1-0ubuntu1.2] (2.8.11.0-0 apt.wxwidgets.org) []
Inst libwxbase2.8-0 [2.8.10.1-0ubuntu1.2] (2.8.11.0-0 apt.wxwidgets.org)
Inst wx-common [2.8.10.1-0ubuntu1.2] (2.8.11.0-0 apt.wxwidgets.org)
Inst wx2.8-doc [2.8.10.1-0ubuntu1.2] (2.8.11.0-0 apt.wxwidgets.org)
Inst wx2.8-examples [2.8.10.1-0ubuntu1.2] (2.8.11.0-0 apt.wxwidgets.org)
Conf wx2.8-headers (2.8.11.0-0 apt.wxwidgets.org)
Conf libwxbase2.8-0 (2.8.11.0-0 apt.wxwidgets.org)
Conf libwxgtk2.8-0 (2.8.11.0-0 apt.wxwidgets.org)
Conf libwxbase2.8-dev (2.8.11.0-0 apt.wxwidgets.org)
Conf libwxgtk2.8-dev (2.8.11.0-0 apt.wxwidgets.org)
Conf wx-common (2.8.11.0-0 apt.wxwidgets.org)
Conf wx2.8-doc (2.8.11.0-0 apt.wxwidgets.org)
Conf wx2.8-examples (2.8.11.0-0 apt.wxwidgets.org)

```

So what's Synaptic's problem?

---

### Post by r.stiltskin on 2011-01-09
Is this just a bug in Synaptic?  I definitely installed the repo's gpg key, and apt-get installed the programs with no complaints at all.  A little while later, I imported another repository, LGP Ubuntu repository ([http://lgp203.free.fr/ubuntu](http://lgp203.free.fr/ubuntu)) and installed a new build of CodeBlocks from there using Synaptic, and it had no problem with that one.

Or is there some discernable reason for Symantic's problem with wxpython.org?  Is there any documentation that spells out exactly what the criteria are?  All I can find are sort of vague 'word of mouth' comments about these warnings.

---

