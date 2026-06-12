---
title: "Very stale dependency in linux-source"
date: 2011-09-23
forum: General Help
---

### Post by Ibidem on 2011-09-23
This issue is confirmed on Lucid, but I think it affects more recent versions as well.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576229](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576229)
linux-source-2.6 suggests libqt3-dev (for make xconfig).  This package was renamed libqt3-mt-dev several years ago.
It's a packaging issue, but I haven't had any luck getting that across.

---

