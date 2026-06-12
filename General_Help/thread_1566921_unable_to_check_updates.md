---
title: "unable to check updates"
date: 2010-09-03
forum: General Help
---

### Post by konjeng on 2010-09-03
when i try to check for updates the following problem shows up

Failed to fetch [http://ppa.launchpad.net/network-manager…/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/network-manager…/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/network-manager…/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/network-manager…/dists/karmic/main/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


please help!!!

Thanks in advance.....

---

### Post by Elfy on 2010-09-03
Go to Software Sources - find the two that fail and edit them, they should read like this it seems

[http://ppa.launchpad.net/network-manager/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/network-manager/ubuntu/dists/karmic/main/binary-i386/Packages.gz)

[http://ppa.launchpad.net/network-manager/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/network-manager/ubuntu/dists/karmic/main/source/Sources.gz)

---

