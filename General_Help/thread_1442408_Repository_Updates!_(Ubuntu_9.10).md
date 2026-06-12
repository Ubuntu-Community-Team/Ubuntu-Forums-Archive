---
title: "Repository Updates! (Ubuntu 9.10)"
date: 2010-03-29
forum: General Help
---

### Post by trixa_13 on 2010-03-29
Help! When I opened the terminal and put this command:

[COLOR=Blue]sudo apt-get update[/COLOR]

The PPAs in Software Sources get updated. However, there is one PPA which got this error:

[COLOR=Red]404  Not Found[/COLOR]

This is the PPA which got that error:

[COLOR=Blue]Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages[/COLOR]

At the end, I got this error:

[COLOR=Red]W: Failed to fetch [http://ppa.launchpad.net/trixa-daily/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/trixa-daily/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]

What to do???

---

### Post by the yawner on 2010-03-30
Just disable the PPA repo on your software sources for the meantime. Looks like the file does not exist.

---

