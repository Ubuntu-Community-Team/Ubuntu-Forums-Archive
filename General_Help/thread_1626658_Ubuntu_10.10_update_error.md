---
title: "Ubuntu 10.10 update error"
date: 2010-11-20
forum: General Help
---

### Post by bnorthrup333 on 2010-11-20
Ever since I updated from ubuntu 10.04 to ubuntu 10.10 I keep on getting the same error messages when I check the update manager:

Failed to fetch [http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I would greatly appreciate any help I receive

---

### Post by Elfy on 2010-11-20
Those PPAs are pointing at a maverick version - there isn't one.

[http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/](http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/)

Remove them from your sources.

Go to Software Sources in the sys admin menu (~if you don't have that you can access it from synaptic in the same menu - in the settings tab.

---

### Post by bnorthrup333 on 2010-11-20
Thanks for the help it worked:D

---

