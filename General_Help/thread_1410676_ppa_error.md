---
title: "ppa error"
date: 2010-02-19
forum: General Help
---

### Post by majest on 2010-02-19
I wanted to update to OpenOffice 3.2, which was not yet available on the default apt-get repositories. So I followed the instructions on some guys blog how to do it.... needless to say it didn't work. But now i get an warning whenever I sudo apt-get update.

```
W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I looked in /etc/apt/sources.list and there is no sign of the address causing the problem. How can I reset the ppa (whatever) list or edit it to remove the wrong entry?

---

### Post by plucky on 2010-02-19
> **majest said:**
> I wanted to update to OpenOffice 3.2, which was not yet available on the default apt-get repositories. So I followed the instructions on some guys blog how to do it.... needless to say it didn't work. But now i get an warning whenever I sudo apt-get update.

```
W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I looked in /etc/apt/sources.list and there is no sign of the address causing the problem. How can I reset the ppa (whatever) list or edit it to remove the wrong entry?


There is no "karmic" distribution at that location.

See [here](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/)

Good Luck

---

### Post by majest on 2010-02-19
Well I found out how to remove it.

Start Menu -> Ubuntu Software Center -> Edit -> Software Sources -> Other Software: remove

---

### Post by Julita on 2010-02-19
You can install .deb packages directly from [http://download.services.openoffice.org/files/localized/en-GB/3.2.0/OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz](http://download.services.openoffice.org/files/localized/en-GB/3.2.0/OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz)
unpack them, go to the directory DEBS, cd there and install via
sudo dpkg -i *.deb

---

