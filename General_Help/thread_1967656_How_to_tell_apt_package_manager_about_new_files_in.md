---
title: "How to tell apt package manager about new files in /var/cache?"
date: 2012-04-28
forum: General Help
---

### Post by chortle on 2012-04-28
I lost my Ubuntu 11.10 installation and had to upgrade to 12.04 over the top. Before this I extracted my own files and made a copy of the packages I had already downloaded from

/var/cache/apt/archives/

My internet is slow, so I didn't want to download all those again. After installation, I put those packages back into the archives directory. How do I inform apt that these packages are now in that directory?

---

### Post by Cheesemill on 2012-04-28
I don't think you have to.

If you try and install a package that is already in the cache it will use the local copy.

---

