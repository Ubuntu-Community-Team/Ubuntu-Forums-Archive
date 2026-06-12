---
title: "What does this mean?"
date: 2011-03-19
forum: General Help
---

### Post by unbuntunewb on 2011-03-19
Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I have been getting this for a while now complete with a red triangle with an ! in it on the panel.

---

### Post by NumPy on 2011-03-19
> **unbuntunewb said:**
> Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I have been getting this for a while now complete with a red triangle with an ! in it on the panel.

It means the entry in /etc/apt/sources.list is not valid. The entry itself if pointing to a ppa (launchpad) managed package ilap. Following the link it has changed to maverick, and not lucid. You can either comment it out, or delete it. They no longer have lucid packages in that branch.

---

