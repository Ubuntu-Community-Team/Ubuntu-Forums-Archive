---
title: "'Could not initialize the package information' Update Manager"
date: 2010-08-06
forum: General Help
---

### Post by theory7716 on 2010-08-06
'Could not initialize the package information'

When I 'sudo apt-get update'

Reading package lists... Error!
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
david@David:~$ sudo apt-get dist-upgrade
Reading package lists... Error!
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-updates_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by vmguru007 on 2011-06-15
Hi,

I believe this is similar to the problem I had earlier today, and fixed it by following the instruction posted on the following article:

[http://www.linux2aix.com/linux/ubuntu/ubuntu-1104-update-manager-could-not-initialize-the-package-information.html](http://www.linux2aix.com/linux/ubuntu/ubuntu-1104-update-manager-could-not-initialize-the-package-information.html)

Please let me know if this work for you.

Enjoy,
Erick
[http://www.TSMGuru.com](http://www.TSMGuru.com)

---

