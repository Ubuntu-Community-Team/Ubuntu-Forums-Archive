---
title: "Update vs Upgrade"
date: 2009-09-15
forum: General Help
---

### Post by alligoodw on 2009-09-15
Using the terminal, what is the difference between these two commands?

sudo apt-get update
sudo apt-get upgrade

---

### Post by lisati on 2009-09-15
From **man apt-get**:
> update
           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.

       upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.


---

### Post by Rob_H on 2009-09-15
Put another way, *update* does not make any changes to the set of installed packages, it merely checks to see what's new. Whereas *upgrade* does.

---

### Post by alligoodw on 2009-09-15
This answers my question.  I appreciate the education from the both of you.

---

### Post by tgalati4 on 2009-09-15
dist-upgrade is what you want to avoid.

It moves you from say Hardy to Intrepid.  You can expect breakage when that happens.

---

### Post by CatKiller on 2009-09-15
> **tgalati4 said:**
> dist-upgrade is what you want to avoid.

It moves you from say Hardy to Intrepid.  You can expect breakage when that happens.

No you don't. dist-upgrades are fine. That's why they are there.

---

