---
title: "Update Manager Problems"
date: 2011-10-31
forum: General Help
---

### Post by hybridxdawn on 2011-10-31
I've been upgraded to 11.10 for a few weeks now, but just recently i've been getting this error:

W:Failed to fetch [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

What's up with that?

---

### Post by dcstar on 2011-10-31
> **hybridxdawn said:**
> I've been upgraded to 11.10 for a few weeks now, but just recently i've been getting this error:

W:Failed to fetch [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

What's up with that?

It means that PPA is no longer available. Delete it out of your system repositories.

---

### Post by hybridxdawn on 2011-10-31
thanks!

apologies, but how would i go about doing that?

---

### Post by Script Warlock on 2011-10-31
launch ubuntu software center > edit > software sources > other software

---

### Post by hybridxdawn on 2011-10-31
thanks!

---

