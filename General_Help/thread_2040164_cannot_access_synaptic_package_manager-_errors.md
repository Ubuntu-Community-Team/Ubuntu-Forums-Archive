---
title: "cannot access synaptic package manager- errors"
date: 2012-08-10
forum: General Help
---

### Post by dingdowner on 2012-08-10
Suddenly, after a recent update,( Ubuntu 10.04, kernel version 2.6.32-42) I cannot access Synaptic package manager!
I get the following error which has no way out except to close the error message window. Any ideas?
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by johnathansmith on 2012-08-10
Look at the post number #18  from [Launchpad]("https://answers.launchpad.net/ubuntu/+source/apt/+question/180429")
```

sudo fuser -vvv /var/lib/dpkg/lock
sudo rm /var/lib/apt/lists/lock
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists
sudo rm /var/cache/apt/*.bin
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
LANG=C;sudo apt-get clean
LANG=C;sudo apt-get autoclean
LANG=C;sudo apt-get --purge autoremove
LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824
sudo dpkg --clear-avail
sudo dpkg --configure -a
LANG=C;sudo apt-get -f install
LANG=C;sudo apt-get --fix-missing install
LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824 && sudo apt-get dist-upgrade

May fix your packages
```

---

